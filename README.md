# C# MySql Wrapper

### Installation
Download MySql connector [here](https://dev.mysql.com/downloads/connector/net/1.0.html) and add "MySql.Data.dll" to the project references then upload "MySql.cs" to your project folder.

### Initialization
```c#
MySqlWrapper database = new MySqlWrapper("localhost", "username", "password", "database_name");
```
### Open Connection
```c#
database.Open();
```

### Connection State
```c#
var dbstate = database.State();
console.writeline(dbstate);
```
or
```c#
console.writeline(database.State());
```
or any other way it fits ur scenario.
### Close Connection
```c#
database.Close();
```

### Insert Query
```c#
var Data = new Dictionary<string, string>{
    ["firstname"] = "John",
    ["lastname"] = "Smith",
    ["age"] = "24"
};

database.Table("demo").Insert(Data);
```

### Update Query
```c#
var Data = new Dictionary<string, Dictionary<string, string>>{
    ["age"] = new Dictionary<string, string>{
        ["="] = "24"
    }
};
var Entry = new Dictionary<string, string>{
    ["lastname"] = "Johnson"
};

database.Table("demo").Where(Entry).Update(Data);
```

### Select Query
```c#
var Data = new Dictionary<string, Dictionary<string, string>>{
    ["lastname"] = new Dictionary<string, string>{
        ["="] = "John"
    }
};

database.Table("demo").Where(Data).Get();
```

### Delete Query
```c#
var Data = new Dictionary<string, Dictionary<string, string>>{
    ["age"] = new Dictionary<string, string>{
        ["="] = "24"
    }
};

database.Table("demo").Where(Data).Delete();
```

### Where condition
```c#
var Data = new Dictionary<string, Dictionary<string, string>>{
    ["firstname"] = new Dictionary<string, string>{
        ["="] = "John"
    },
    ["age"] = new Dictionary<string, string>{
        [">"] = "18",
        ["<="] = "24"
    }
};

database.Table("demo").Where(Data).Get();
```
