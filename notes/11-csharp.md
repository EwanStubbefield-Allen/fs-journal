# CSharp

<!-- SECTION Basics -->
  int variable = 4;
  double variable = 3.14;
  int[] variables = { 1, 2, 3 };
  bool variable = false;

  if (has to be bool)
  {}

  for(int i = 0; i < list.Length; i++)
  {
    int l = list[i];
  }

  Console.WriteLine($"string {variable}")

<!-- SECTION String Methods -->
  char variable = 'v';
  string variable = "variable";
  string.ToUpper() --> Uppercase all character

<!-- SECTION List Methods -->
  List<T> list = new List<T>(); --> Creates List with type
  list.Add(3); --> Adds 3 to List
  list.Remover(3); --> Removes first instance from List
  list.Find(l => conditional) --> Returns first item that matches condition
  list.AddRange(listB) --> Adds another list to original list
  list.BinarySearch() --> Returns the index of a value that matches the params
  list.Clear() --> Removes all items from list
  list.Contains() --> Returns true if list contains value

  foreach(int l in list)
  {}

<!-- SECTION Startup -->
  services.AddScoped<NamesRepository>();
  services.AddScoped<NamesService>();

<!-- SECTION Controller -->
  [Authorize] --> All requests require auth
  [ApiController]
  [Route("api/controller")] --> super controller is Name but lowercased
  public class NamesController : ControllerBase --> : is inheritance
  {
    private readonly NamesService _namesService; --> Readonly is const
    private readonly Auth0Provider _auth0Provider
    public NamesController(NamesService namesService, Auth0Provider auth0provider) --> Constructor
    {
      _namesService = namesService; --> Implied this
      _auth0Provider = auth0Provider;
    }
    [HttpGet] --> Decorator to say what kind of request
    public ActionResult<List> GetNames() --> Must return type
    {
      try
      {
        List<T> names = _namesService.GetNames();
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpGet("{nameId}")]
    public ActionResult<T> GetNameById(Type nameId)
    {
      try
      {
        Type name = _namesService.GetNameById(nameId);
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpPost]
    [Authorize]
    public async Task<ActionResult<T>> CreateName([FromBody] Type nameData)
    {
      try
      {
        Account userInfo = await _auth0Provider.GetUserInfoAsync<Account>(HttpContext);
        nameData.accountId = userInfo.id;
        Type name = _namesService.CreateName(nameData);
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpPut("{nameId}")]
    [Authorize]
    public Task<ActionResult<T>> UpdateName(Type nameId, [FromBody] Type nameData)
    {
      try
      {
        Account userInfo = await _auth0Provider.GetUserInfoAsync<Account>(HttpContext);
        nameData.accountId = userInfo.id;
        nameData.Id = nameId;
        Name name = _namesService.UpdateName(nameData);
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpDelete("{nameId}")]
    [Authorize]
    public ActionResult<string> RemoveName(Type nameId)
    {
      try
      {
        Account userInfo = await _auth0Provider.GetUserInfoAsync<Account>(HttpContext);
        Type name = _namesService.RemoveName(nameId, userInfo.id);
        return Ok("Name was deleted");
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
  }

<!-- SECTION Service -->
  public class NamesService
  {
    private readonly NamesRepository _namesRepository;
    public NamesService(NamesRepository namesRepository)
    {
      _namesRepository = namesRepository;
    }
    internal List<T> GetNames() --> internal is only public to assembly
    {
      return _namesRepository.GetNames();
    }
    internal Type GetNameById(Type nameId)
    {
      Type name = _namesRepository.GetNameById(nameId)
      return name ?? throw new Exception($"[NO NAME MATCHES THE ID: {nameId}]");
    }
    internal Type CreateName(Type nameData)
    {
      Type nameId = _namesRepository.CreateName(nameData);
      return GetNameById(nameId);
    }
    internal Type UpdateName(Type nameData)
    {
      Type originalName = GetNameById(nameDataId);
      originalName.Value = nameData.Value ?? original.Value;
      return _namesRepository.UpdateName(originalName);
    }
    internal Type RemoveName(Type nameId, string accountId)
    {
      Type name = GetNameById(nameId);
      if (name.accountId != accountId)
      {
        throw new Exception("[YOU ARE NOT THE CREATOR OF THIS!]")
      }
      _namesRepository.RemoveName(nameId);
      return name;
    }
  }

<!-- SECTION Repository -->
  public class NamesRepository
  {
    private readonly IDbConnection _db;
    public NamesRepository(IDbConnection db)
    {
      _db = db;
    }
    internal List<T> GetNames()
    {
      string sql = @"
      SELECT tab.* , acc.*
      FROM table_name tab
      JOIN accounts acc ON acc.id = tab.accountId
      ;";
      return _db.Query<T, Profile, T>( --> First two what you get and last what you give
      sql,
      (name, profile) => { --> Maps name and profile to combine into nested object
        name.profile = profile;
        return name;
      }
      ).ToList();
    }
    internal Type GetNamesById(Type nameId)
    {
      string sql = @"
      SELECT tab.* , acc.*
      FROM table_name tab
      JOIN accounts acc ON acc.id = tab.accountId
      WHERE tab.id = @nameId;"; --> @ sanitizes strings
      return _db.Query<T, Profile, T>( --> Use query because multiple tables(T and profile)
        sql, 
        (name, profile) => {
          name.profile = profile;
          return name
        }
        new { nameId }).FirstOrDefault();
    }
    internal Type CreateName(Type nameData)
    {
      string sql = @" --> Allows multiline string
      INSERT INTO table_name ( column, etc. )
      VALUES ( @Value, etc. );
      SELECT LAST_INSERT_ID();
      ;";
      return _db.ExecuteScalar<T>(sql, nameData); --> Runs sql command and returns one value
    }
    internal Type UpdateName(Type originalName)
    {
      string sql = @"
      UPDATE table_name SET
      column = @Value
      WHERE id = @Id LIMIT 1;
      SELECT * FROM table_name WHERE id = @Id
      ;";
      Type name = _db.QueryFirstOrDefault(sql, originalName);
      return name;
    }
    internal void RemoveName(Type nameId)
    {
      string sql = "DELETE FROM table_name WHERE id = @nameId LIMIT 1;";
      _db.Execute(sql, new { nameId });
    }
  }

<!-- SECTION Model -->
  public class Name
  {
    public type Value { get; set; } --> Declaring variables
    public int? Number { get; set; } --> If no number then it set number to null
    public bool? Boolean { get; set; } --> If no bool then it set bool to null
    public Profile profile { get; set; } --> Allows nested objects
  }