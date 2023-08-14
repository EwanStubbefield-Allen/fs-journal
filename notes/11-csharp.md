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
    public NamesController(NamesService _namesService)
    {
      _namesService = namesService
    }
    [HttpGet] --> Decorator to say what kind of request
    public ActionResult<List> GetNames() --> Must return type
    {
      try
      {
        List<T> names = _namesService.GetNames()
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
        Name name = _namesService.GetNameById(type nameId);
        return Ok(name)
      }
      catch (Exception e)
      {
        return BadRequest(e.message)
      }
    }
    [HttpPost]
    public ActionResult<T> CreateName([FromBody] Name nameData)
    {
      try
      {
        Name name = _namesService.CreateName(nameData)
        return Ok(name)
      }
      catch (Exception e)
      {
        return BadRequest(e.message)
      }
    }
    [HttpDelete("{nameId}")]
    public ActionResult<T> RemoveName(type nameId)
    {
      try
      {
        Name name = _namesService.RemoveName(nameId)
        return Ok(name)
      }
      catch (Exception e)
      {
        return BadRequest(e.message)
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
    internal List<T> GetNames()
    {
      List<T> names = _namesRepository.GetNames();
      return names
    }
    internal Name GetNameById(Type nameId)
    {
      if (name == null)
      {
        throw new Exception("Error")
      }
      return name;
    }
    internal Name CreateName(Name nameData)
    {
      Name name = _namesRepository.CreateName(nameData)
      return name
    }
    internal Name RemoveName(Type nameId)
    {
      Name name = _namesRepository.RemoveName(nameId)
      return name
    }
  }

<!-- SECTION Repository -->
  public class NamesRepository
  {
    private List<T> names; --> Temp
    public NamesRepository()
    {
      names = new List<T>();
      names.Add(new Name("name", ets.));
    }
    internal List<T> GetNames()
    {
      return names
    }
    internal Name GetNamesById(nameId)
    {
      Name name = names.Find(n => n.id == nameId);
      return name
    }
    internal Name CreateName(Name nameData)
    {
      Names.Add(nameData)
      return nameData
    }
    internal Name RemoveName(Type nameId)
    {
      Name nameData = GetNameById(nameId)
      Names.Remove(nameData)
      return nameData
    }
  }

<!-- SECTION Model -->
  public class Name
  {
    public type Name { get; set; } --> Declaring variables 
    public Name(type name, etc.) --> Constructor
    {
      Name = name; --> Implied this
    }
  }