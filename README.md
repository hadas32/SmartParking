# Smart Parking Management System

## Project Overview
This is a server-side project built with ASP.NET Core 8, designed to manage a smart parking lot.
The system allows managing parking lots, parking spots, vehicles, and calculating payments dynamically.

> **Note:** This project primarily focuses on **Server-side Architecture (N-Tier)** and **Business Logic**.

## Project Description
The system simulates a real-world parking lot:
* **Car Entry:** Automatically assigned the first available spot.
* **Car Exit:** Calculates payment based on time spent and frees the spot.
## Database Structure

### 1. Parking
| Column | Description |
| :--- | :--- |
| Id (PK) | Unique identifier |
| Name | Parking lot name |
| Available_spots | Current free spots |
| Price_per_hour | Hourly rate |

### 2. Spot
| Column | Description |
| :--- | :--- |
| Id (PK) | Unique identifier |
| Is_occupied | Status |
| CarId (FK) | Reference to Car |

## Main API Endpoints
* GET `/api/Parkings` - Get all lots
* POST `/api/Cars` - Register entry
* DELETE `/api/Cars/{id}` - Register exit (JWT Required)
* POST `/api/Auth/login` - Get Admin Token

## Technologies & Architecture
* **Backend:** ASP.NET Core 8.0, C#
* **Architecture:** N-Tier, Dependency Injection
* **Database:** SQL Server, EF Core
* **Security:** JWT Authentication
* **Mapping:** AutoMapper, DTOs
##  Known Issues & Future Improvements

* **Concurrency Handling:** Currently, under extreme high load, a race condition might occur during spot allocation.
* **Planned Fix:** Implement **Optimistic Concurrency** using EF Core (adding a `[Timestamp]` token to the `Spot` entity) to ensure data integrity during parallel requests.

## Developed By
* **Hadas Homri** & **Sara Levin**
