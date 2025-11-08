SixteenClothing – .NET Application Deployment Guide

This README explains how to restore, build, run, and access the SixteenClothing .NET application.

✅ Prerequisites

Install these before running the project:

.NET SDK (LTS version)

Git

Linux/Windows/Mac system

✅ Clone the Repository
git clone <your-repo-url>
cd SixteenClothing

✅ Restore Dependencies

Restores all NuGet packages required for the project.

dotnet restore

✅ Build the Project

Build the application:

dotnet build --configuration Release

✅ Run the Application

Run the app and expose port 5000 to all interfaces:

dotnet SixteenClothing.dll --urls "http://0.0.0.0:5000"


If DLL is inside build folder:

dotnet bin/Release/net8.0/SixteenClothing.dll --urls "http://0.0.0.0:5000"

✅ Verify the Application is Running

Check listening port:

sudo lsof -i -P -n | grep 5000


Expected:

dotnet  8650  srinu  294u  IPv4  TCP *:5000 (LISTEN)

✅ Access the Application
Localhost:
http://localhost:5000

From Browser (Public IP):
http://<public-ip>:5000


✅ Ensure port 5000 is open in firewall
✅ Security groups allow inbound traffic (if VM on cloud)

✅ Run Application in Background (Optional)
nohup dotnet SixteenClothing.dll --urls "http://0.0.0.0:5000" &


Logs → nohup.out

✅ Folder Structure (Example)
SixteenClothing/
│── Controllers/
│── Models/
│── Views/
│── wwwroot/
│── appsettings.json
│── SixteenClothing.csproj
└── Program.cs

✅ Troubleshooting

Port already in use:

sudo lsof -i:5000


Kill old process:

sudo kill -9 <PID>


Allow firewall:

sudo ufw allow 5000
