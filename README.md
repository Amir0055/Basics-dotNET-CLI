# Basics-dotNET-CLI


• Check dotNET version and info 


 `dotnet --info`
![Capture d'écran 2024-01-20 235746](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/002cc5e8-00a2-408e-9a1d-9843721447a6)


• create new dotNET solution (that by default take the folder name as solution ]


_PS D:\dotNET>_ `dotnet new sln`  
![Capture d'écran 2024-01-21 000112](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/a8e3be81-bc63-45d3-ba54-c42b37df14f1)

• faire creation cosole Project 


_PS D:\dotNET>_ `dotnet new console -o DemoApp `

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/311b7140-d9b9-4d61-affb-94c4f83e5f42)

> the .csproj contient the confugiration of that project !!!

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/68466250-327f-468f-aa43-8bb222fd9477)

 
> if u open the solution his empty cause he didn't have any ping reference 


![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/c9241325-477d-47ac-b435-1e3ebbe20071)



==>there is no relation betwen the Solution and the console project Now !!!

• add relation by this cmd 


_PS D:\dotNET>_ ` dotnet sln add DemoApp`

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/65303e10-c497-4578-91a6-3881ef958c9c)
![Capture d’écran (596)](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/2b5e7f01-0ad3-4215-a740-37731427d159)
> if we open the solution as file w find that he add refference to DemoApp cosole Project
![Capture d'écran 2024-01-21 114354](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/cd6e38c1-9cd8-491c-aaee-187d16b5e0a8)


•try add Class Library that will contient the library

 _PS D:\dotNET>_ ` dotnet new classlib -o DemoLib`  //by default is going to be C# //-o [name-output]

 _PS D:\dotNET>_ ` dotnet sln add DemoLib`

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/c4c0d214-0187-448d-9fa8-9090e9cc41e4)

• add package in DemoLib Project
 
 _PS D:\dotNET>_ ` cd DemoLib`

 _PS D:\dotNET\DemoLib>_ ` dotnet add package Dapper`

> try to open .csproj of DemoLib u find that the package he add successfully

![Capture d'écran 2024-01-21 115604](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/84bea887-73e7-431e-979c-e46d67a7f353)
==>there is no relation with DemoLib Project Now (no one can see what he has inside it)!!!

• add reference bettwen DemoApp-->DemoLib


 _PS D:\dotNET>_ ` cd DemoApp`
 _PS D:\dotNET\DemoApp>_ ` dotnet add reference ../DemoLib/demoLib.csproj`//Specifie l'emplacement du .csproj of the project u want to reffer with


![Capture d'écran 2024-01-21 120534](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/effecbb9-33fd-497d-895a-97097b52a7e7)

> if u want to remove reference just remove the 3 line in the red cercle

===> 🔢 we still don't have Bean directory 👍 

1. _PS D:\dotNET\DemoApp>_ ` dotnet restore` //you initiate the process of restoring dependencies for that project in csproj file

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/6b7de090-3a88-4308-9276-7ba438eba53c)

Before Execute the build cmd **D:\dotNET\DemoApp\bin\Debug\net7.0** _is empty_

2. _PS D:\dotNET\DemoApp>_ ` dotnet build`// he will make dotnet restore automatic

![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/d35ddbf3-6308-4d5b-bfc7-b8f804988c9f)

3._PS D:\dotNET\DemoApp>_ ` dotnet clean`//will remove the all temp file 
=>will delete all files in D:\dotNET\DemoApp\bin\Debug\net7.0

4. _PS D:\dotNET\DemoApp>_ ` dotnet run` will make build automatic

* Create OutPut Project  doc microsoft /core/rid-catalog specifier run identifier

 _PS D:\dotNET\DemoApp>_ ` dotnet publish -p:PublishSingleFile=true -r win-x64 --self-contained false`



  ○[PublishSingleFile=true] : mean extratct all file in only One 


  ○[win-x64] :specifier run identifier 


  ○[--self-contained false] :this is mean the app not depended by Library of the framework (.NET.CORE,..) [but u should suppose u have it in the machine u test on it .exe]


( if u dont just turn it true and the size of the .exe he will grow up and will have .NET 7 deppendencie inside it =>run it in any machine doesn't matter)


![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/715a693a-f8a2-4764-a7c1-e39e965442b5)

* dive into the folder created ./publish
![image](https://github.com/Amir0055/Basics-dotNET-CLI/assets/93008466/56b57252-61c4-4f2d-a28d-b5b5ee85b983)

♦ _**DemoApp.exe**_ :executable file 

♦ _**DemoApp.pdb**_ :debuging in production file(in real time)

♦ _**DemoLib.pdb**_ :debuging in production file(in real time)


