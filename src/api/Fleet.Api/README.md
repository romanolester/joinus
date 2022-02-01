# Fleet Backend

This folder contains the backend for the take-home exercise.

# Technical Details

The backend consists of a .NET 6.0 project and uses EF Core 6.0 against an SQLite provider. Make sure you have the .NET 6.0 SDK installed. Then navigate to the API project folder and run `dotnet run` or `dotnet watch run` on the project.

The `Fleet.Vehicles` project contains the core classes needed to support the exposed endpoints under `Fleet.Api`. All models, repositories, view models, and services are contained within this project.

A seeded database, `fleet.db`, is already included in the solution under the `Fleet.Api` folder. You may use any SQLite browser to browse through the database. You can convert this to any database provider you want if you wish to, be it in-memory or otherwise.

# Task

For the backend part of the exercise, you are to add a few endpoints to support a new feature: end-of-day vehicle logs. A file will be sent to the backend which contains a list of vehicles and their last known location and timestamp. You will need to save these information so that it can be displayed in the map afterwards.

You may choose to implement this however you like: use any NuGet packages, rewrite the project in your framework of choice, restructure the solution, split it into microservices, change the database provider, combine it into a single project, or whatever your imagination can produce.

You may choose to focus 100% of your energy on the backend, in which case, please provide sample Postman requests. You may go above and beyond the basic requirements to demonstrate in-depth technical knowledge and product design chops.

# Changelog
- Added Logging, HttpLogging for both the request and response and Error logging
- Added Exception Handling, properly handle the exceptions and make sure not to return it to the client application.
- Added a new endpoint named ("api/vehicles/logs/csv") for end of day upload of vehicle locations. This endpoint uses the same business logic with ("api/vehicles/logs") both of them have the ability to create new vehicle record and update vehicle logs.
- Added configurations:
  - FileUpload.AcceptedFileName, accepted filename for end of day upload
  - FileUpload.AcceptedFilePath, file path to store accepted end of day files
  - FileUpload.RejectedFilePath, file path to store rejected end of day files

# How to run and test the app

1. Run `dotnet run` or `dotnet watch run` on the project.
2. Import the [Postman collection](../../tools/postman_collection/joinus.postman_collection.json) to a Postman application (preferably version 2.1).
3. Open 'Upload CSV EOD' request and go to Body tab. Change value for the file and select the proper file. You can use the [sample file](../../tools/sample_csv/vehicle_eod.csv) and update the values accordingly.
4. Execute 'Upload CSV EOD' request to test.