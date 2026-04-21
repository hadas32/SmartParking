# Smart Parking Management System

## Project Overview

This is a server-side project built with ASP.NET Core 8, designed to manage a smart parking lot.
The system allows managing parking lots, parking spots, vehicles, and calculating payments dynamically based on the duration of the parking.

> **Note:** This project primarily focuses on **Server-side Architecture (N-Tier)** and **Business Logic**. The frontend was developed for demonstration purposes only to showcase the API's capabilities.

## Project Description

The system simulates a real-world parking lot.
When a car enters, it is registered in the system and automatically assigned the first available parking spot.
When it exits, the system calculates the payment according to the time spent and frees the spot.

The system includes three main entities:
* **Parking** – represents the parking lot.
* **Spot** – represents an individual parking spot.
* **Car** – represents the registered vehicle.

## Database Structure

### 1. Parking
| Column | Description |
| :--- | :--- |
| Id (PK) | Unique identifier for the parking lot |
| Name | Parking lot name |
| Location | Address or location |
| Total_spots | Total number of parking spots |
| Available_spots | Number of currently available spots |
| Price_per_hour | Parking fee per hour |

### 2. Spot
| Column | Description |
| :--- | :--- |
| Id (PK) | Unique identifier for the spot |
| ParkingId (FK)| Foreign key referencing Parking |
| Spot_number | Parking spot number |
| Is_occupied | Indicates whether the spot is occupied |
| CarId (FK) | Foreign key referencing Car (nullable) |

### 3. Car
| Column | Description |
| :--- | :--- |
| Id (PK) | Unique identifier for the car |
| License_num | Car license number |
| Owner_name | Full name of the car owner |
| Entry_time | Time of entry |
| Exit_time | Time of exit |
| Total_payment | Total payment for the parking session |

## Main API Endpoints (RESTful)
| Method | Route | Description |
| :--- | :--- | :--- |
| GET | `/api/Parkings` | Get all parking lots |
| POST | `/api/Parkings` | Add a new parking lot (Requires JWT Auth) |
| GET | `/api/Spots` | Retrieve all parking spots |
| POST | `/api/Cars` | Register a car entry and assign a spot |
| DELETE | `/api/Cars/{id}`| Register a car exit, calculate payment, and free the spot (Requires JWT Auth) |
| POST | `/api/Auth/login` | Authenticate admin and generate JWT Token |

## Business Logic

* **Car Entry:** The system validates parking availability, finds the first available spot, marks it as occupied, stores the car’s entry time, and decrements available spots.
* **Car Exit:** The system calculates the total time spent (rounding up to the nearest hour), computes the payment according to the specific parking's hourly rate, and frees the parking spot.

## Technologies & Architecture

* **Backend:** ASP.NET Core 8.0, C#
* **Architecture:** N-Tier Architecture, Dependency Injection (DI)
* **Database:** SQL Server, Entity Framework Core (Code-First)
* **Security:** JWT Authentication
* **Mapping:** AutoMapper, DTOs
* **Documentation:** Swagger UI

## Developed By
* **Sara Levin**
* **Hadas Homri**

---

## Installation & Setup

Follow these steps to clone the repository and run the project locally.

### 1. Clone the Repository
Open your terminal and run the following commands to download the project:
```bash
git clone https://github.com/saralev111/SmartParking.git
cd SmartParking
