# Library System API - Bug Documentation

This is a buggy Library Management System API built with .NET and n-tier architecture. The system contains **20 intentional bugs** across different layers (Models, Repositories, Services, Controllers, and Configuration).

## Architecture

The application follows n-tier architecture:
- **Models Layer**: Data models (Book, Member, Transaction)
- **Repository Layer**: Data access logic
- **Service Layer**: Business logic
- **Controller Layer**: API endpoints
- **Program.cs**: Dependency injection configuration

---

## Please List all of the bugs you find & where you found it


### EXAMPLE **Bug #1: Wrong HTTP Request method in MemberController**
**Location**: `Controllers/MemberController.cs` - Line 38  
**Type**: API Design Error  

**Bug**:
```csharp
    [HttpDelete("{id}")]
    public ActionResult<Member> Update(int id, [FromBody] Member member)
```

## 1. Bug - 
/usr/local/share/dotnet/sdk/9.0.305/Sdks/Microsoft.NET.Sdk/targets/Microsoft.NET.TargetFrameworkInference.targets(166,5): error NETSDK1045: The current .NET SDK does not support targeting .NET 10.0.  Either target .NET 9.0 or lower, or use a version of the .NET SDK that supports .NET 10.0. Download the .NET SDK from https://aka.ms/dotnet/download
**Location** Line-10 
**Type**Version Mismatch Error.
fixed -9.0.*-dotnet restore

## 2 Bug-  Newline in constant
**Location** /MemberRepository.cs(23,69): error CS1010:
Fixed Bug - Operator-"


## 3 Bug- Cannot implicitly convert type 'string' to 'bool'
**Location** BookRepository.cs(37,47): error CS0029:
Fixed Bug - Operator ==


## 4 Bug- Cannot implicitly convert type 'string' to 'bool'
**Location** MemberRepository.cs(40,49): error CS0029: 
Fixed Bug - Operator ==



## 5 Bug- A previous catch clause already catches all exceptions of this or of a super type ('ArgumentException')
**Location** BooksController.cs(69,20): error CS0160:
Fixed Bug - removed extra catch (ArgumentNullException ex)
            fixed Bug-  catch (ArgumentNullException ex)
            {
                return BadRequest(ex.Message);
            }
            catch (ArgumentException ex)
            {
                return BadRequest(ex.Message);
            }
        


## 6 vel-4/Assignments/BuggyBackend/Properties/launchSettings.json...
Unhandled exception. System.AggregateException: Some services are not able to be constructed (Error while validating the service descriptor 'ServiceType: BuggyBackend.Services.IBookService Lifetime: Scoped ImplementationType: BuggyBackend.Services.BookService': Unable to resolve service for type 'BuggyBackend.Repositories.IBookRepository' while attempting to activate 'BuggyBackend.Services.BookService'.) (Error while validating the service descriptor 'ServiceType: BuggyBackend.Services.ILibraryService Lifetime: Scoped ImplementationType: BuggyBackend.Services.LibraryService': Unable to resolve service for type 'BuggyBackend.Repositories.IBookRepository' while attempting to activate 'BuggyBackend.Services.LibraryService'.)
**Location** programme.cs
Fixed Bug -builder.Services.AddScoped<IBookRepository, BookRepository>();



## 7 Bug- Non-nullable property 'Name' must contain a non-null value when exiting constructor. 
**Location** models/Member.cs(7,23) (6,23):(8,23) warning CS8618:  warning CS8618:warning CS8618:
Fixed Bug -?


## 8 Bug- Non-nullable property 'Name' must contain a non-null value when exiting constructor. 
**Location** models/Book 
Fixed Bug -?

##9 bug - Bookcontroller http get & delete id converted to ID type INT

##10 bug - replaced search with "search " to "SearchByTitle"



API Postman -http://localhost:5273/api/books=Get

http://localhost:5273/api/books/1=get

Create new book-http://localhost:5273/api/books

postman => https://buggybackend-czfrfggec3hxcacg.westus3-01.azurewebsites.net/api/books

getById=>https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/1

Get by search => https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/search?title=1984

get available => https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/available

post create=>https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/
raw:
{
    "title": "not me",
    "author": "praveen",
    "isbn": "123",
    "isAvailable": true
}

putById= https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/2

delete=https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/books/7

Library Controller
post Barrow:
https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/library/borrow
Raw:
{
    "memberId": 1,
    "bookId": 3
}

Get

        [HttpGet("transactions/member/{memberId}")]=====https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Library/transactions/member/1

Get
        [HttpGet("transactions/active")]===https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Library/transactions/active


Get         [HttpGet("overdue")]==https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Library/overdue======>notworking



MemebersController=

Get        
 [HttpGet]==https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Members

         [HttpGet("{id}")]===https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Members/1



        [HttpGet("email/{email}")]===https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Members/email/jmartenezlopez@sjcoe.net


   Post Create ==>
   https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/members
   {
    "name": "Pallavi Pattanashetti",
    "email": "pallavi.dev@example.com"
}

             [HttpPut("{id}")]===https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/Members/1

Delete-
https://newbuggybackendpp-dpgya5bjekbqdheh.westus3-01.azurewebsites.net/api/members/4
