https://github.com/dotnet/winforms/blob/master/Documentation/winforms-designer.md

md SimpleWinForms
cd SimpleWinForms
dotnet new winforms -n SimpleWinForms
dotnet new sln
dotnet sln add SimpleWinForms

dotnet run --project SimpleWinForms\SimpleWinForms.csproj

Open SimpleWinForms.sln

Open the SimpleWinForms project file by double clicking on it in Solution Explorer. Change the TargetFramework property from:

-    <TargetFramework>netcoreapp5.0</TargetFramework>
+    <TargetFrameworks>net472;netcoreapp5.0</TargetFrameworks>
Add for any and every form file you have in this ItemGroup:

 <ItemGroup Condition="'$(TargetFramework)' == 'net472'">
   <Compile Update="Form1.cs">
     <SubType>Form</SubType>
   </Compile>
   <Compile Update="Form1.Designer.cs">
     <DependentUpon>Form1.cs</DependentUpon>
   </Compile>
 </ItemGroup>

注释掉入口文件的这一行
             //Application.SetHighDpiMode(HighDpiMode.SystemAware);
