# .NET on OSX

## Install .NET Version Manager (DNVM)
```
brew tap aspnet/dnx
brew update
brew install dnvm
mkdir ~/.dnx #if it doesn't already exist
source dnvm.sh
```

## Install .NET Core Execution Environment (DNX)
```
dnvm upgrade -u
dnvm install -r coreclr latest -u
```

## write your first app :)
```
cd ~/workspace/dotnet/myfirstapp
```

### create C# file

```
vi HelloWorld.cs
```
### Save this in the file
```
using System;

        public class Program {
        	public static void Main(string[] args){
        		Console.WriteLine("Hello World from Core CLR!");
        	}
        }
```
### create project json
```
vi project.json
```
### Save this in the file
```
{
         "version": "1.0.0-*",
         "dependencies": {
         },
         "frameworks" : {
             "dnx451" : { },
             "dnxcore50" : {
                 "dependencies": {
                     "System.Console": "4.0.0-beta-*"
                 }
             }
         }
     }
```
## Test the awesome new .NET app
```
dnvm list # to get the [version]
dnvm use [version] -r mono
dnu restore
dnvm use [version] -r coreclr
dnx run
```
## If all worked well, here is the output

```
➜  myfirstapp  dnx run
Hello World from Core CLR!
```

## For an IDE, I'm testing monodevelop

http://www.monodevelop.com/download/
