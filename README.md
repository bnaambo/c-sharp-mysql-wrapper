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
database.State();
```

### Close Connection
```c#
database.Close();
```

### Insert Query
```c#
var insertData = new Dictionary<string, string>{
    ["firstname"] = "John",
    ["lastname"] = "Smith",
    ["age"] = "24"
};

database.Table("demo").Insert(insertData);
```

### Update Query
```c#
var whereUpdate = new Dictionary<string, Dictionary<string, string>>{
    ["age"] = new Dictionary<string, string>{
        ["="] = "24"
    }
};
var updateData = new Dictionary<string, string>{
    ["lastname"] = "Johnson"
};

database.Table("demo").Where(whereUpdate).Update(updateData);
```

### Select Query
```c#
var whereGet = new Dictionary<string, Dictionary<string, string>>{
    ["lastname"] = new Dictionary<string, string>{
        ["="] = "John"
    }
};

database.Table("demo").Where(whereGet).Get();
```

### Delete Query
```c#
var whereDelete = new Dictionary<string, Dictionary<string, string>>{
    ["age"] = new Dictionary<string, string>{
        ["="] = "24"
    }
};

database.Table("demo").Where(whereDelete).Delete();
```

### Where condition
```c#
var whereAdvanced = new Dictionary<string, Dictionary<string, string>>{
    ["firstname"] = new Dictionary<string, string>{
        ["="] = "John"
    },
    ["age"] = new Dictionary<string, string>{
        [">"] = "18",
        ["<="] = "24"
    }
};

database.Table("demo").Where(whereAdvanced).Get();
```
