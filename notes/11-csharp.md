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
  [ApiController]
  [Route("api/controller")] --> super controller is Name but lowercased
  public class NamesController : ControllerBase --> : is inheritance
  {
    private readonly NamesService _namesService; --> Readonly is const
    public NamesController(NamesService namesService) --> Constructor
    {
      _namesService = namesService; --> Implied this
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
        Type name = _namesService.GetNameById(type nameId);
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpPost]
    public ActionResult<T> CreateName([FromBody] Type nameData)
    {
      try
      {
        Type name = _namesService.CreateName(nameData);
        return Ok(name);
      }
      catch (Exception e)
      {
        return BadRequest(e.message);
      }
    }
    [HttpPut("{nameId}")]
    public ActionResult<T> UpdateName(Type nameId, [FromBody] Type nameData)
    {
      try
      {
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
    public ActionResult<string> RemoveName(Type nameId)
    {
      try
      {
        Type name = _namesService.RemoveName(nameId);
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
      List<T> names = _namesRepository.GetNames();
      return names;
    }
    internal Name GetNameById(Type nameId)
    {
      if (name == null)
      {
        throw new Exception($"[NO NAME MATCHES THE ID: {nameId}]");
      }
      return name;
    }
    internal Name CreateName(Type nameData)
    {
      Type nameId = _namesRepository.CreateName(nameData);
      Type name = GetNameById(nameId);
      return name;
    }
    internal Name UpdateName(Type nameData)
    {
      Type originalName = GetNameById(nameDataId);
      originalName.Value = nameData.Value ?? original.Value;
      Type name = _namesRepository.UpdateName(originalName);
      return name;
    }
    internal Type RemoveName(Type nameId)
    {
      Type name = GetNameById(nameId);
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
      string sql = "SELECT * FROM table_name;";
      List<T> name = _db.Query<T>(sql).ToList();
      return name;
    }
    internal Name GetNamesById(Type nameId)
    {
      string sql = $"SELECT * FROM table_name WHERE id = @nameId;"; --> @ sanitizes strings
      Type name = _db.QueryFirstOrDefault<T>(sql, new { nameId });
      return name;
    }
    internal Type CreateName(Type nameData)
    {
      string sql = @" --> Allows multiline string
      INSERT INTO table_name ( column, etc. )
      VALUES ( @Value, etc. );
      SELECT LAST_INSERT_ID();
      ;";
      Type nameId = _db.ExecuteScalar<T>(sql, nameData); --> Runs sql command and returns one value
      return nameId;
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
  }