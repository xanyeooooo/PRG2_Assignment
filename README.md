# Changi Airport Terminal 5 Flight Management System (Academic Assignment)

A console-based simulated flight management system developed in C# as part of a programming assignment. The system models airline operations, flights, and boarding gate management for Changi Airport Terminal 5 in an academic context and is not associated with real-world airport systems.

## 📋 Project Information

**Course**: Programming 2 (PRG2)  
**Student**: Xander Yeo Kai Kiat
**Partner**: Teo Yun Nise Kieira

## 🎯 Features

### Core Features
1. **List All Flights** - Display all flights with airline information, origin, destination, and expected times
2. **List Boarding Gates** - View all boarding gates and their special request support capabilities
3. **Assign Boarding Gate to Flight** - Manually assign flights to available boarding gates with status updates
4. **Create Flight** - Add new flights with validation and automatic airline association
5. **Display Airline Flights** - View all flights operated by a specific airline
6. **Modify Flight Details** - Update flight information including origin, destination, time, status, special requests, and boarding gates
7. **Display Flight Schedule** - View all flights sorted by expected arrival/departure time
8. **Display Total Fees** - Calculate and display comprehensive fee breakdown per airline with discounts

### Additional Features
- **Bulk Processing (Feature a)** - Automatically assign all unassigned flights to compatible boarding gates
- **Advanced Fee Calculation (Feature b)** - Calculate fees with multiple discount rules and detailed breakdowns

## 🏗️ System Architecture

### Class Structure

```
Terminal
├── Airlines (Dictionary)
├── Flights (Dictionary)
├── BoardingGates (Dictionary)
└── GateFees (Dictionary)

Flight (Base Class)
├── NORMFlight (Normal flights)
├── DDJBFlight (Special request: DDJB)
├── CFFTFlight (Special request: CFFT)
└── LWTTFlight (Special request: LWTT)
```

### Key Classes

#### **Terminal**
Manages the entire terminal operations including airlines, flights, and boarding gates.

**Properties:**
- `TerminalName`: Name of the terminal
- `Airlines`: Dictionary of all airlines operating in the terminal
- `Flights`: Dictionary of all flights
- `BoardingGates`: Dictionary of all boarding gates
- `GateFees`: Dictionary for storing gate fees

**Methods:**
- `AddAirline(Airline)`: Add a new airline to the terminal
- `AddBoardingGate(BoardingGate)`: Add a new boarding gate
- `GetAirlineFromFlight(Flight)`: Retrieve airline associated with a flight
- `PrintAirlineFees()`: Display fee breakdown for all airlines

#### **Airline**
Represents an airline operating in the terminal.

**Properties:**
- `Name`: Full name of the airline
- `Code`: Two-letter airline code (e.g., SQ, MH)
- `Flights`: Dictionary of flights operated by this airline

**Methods:**
- `AddFlight(Flight)`: Add a flight to the airline
- `RemoveFlight(Flight)`: Remove a flight from the airline
- `CalculateFees()`: Calculate total fees and discounts for the airline

#### **Flight (Base Class)**
Base class for all flight types.

**Properties:**
- `FlightNo`: Unique flight number
- `Origin`: Origin airport
- `Destination`: Destination airport
- `ExpectedTime`: Expected departure/arrival time
- `Status`: Current flight status

**Subclasses:**
- `NORMFlight`: Standard flights without special requests
- `DDJBFlight`: Flights with DDJB special request (+$300 fee)
- `CFFTFlight`: Flights with CFFT special request (+$150 fee)
- `LWTTFlight`: Flights with LWTT special request (+$500 fee)

#### **BoardingGate**
Represents a boarding gate with special request capabilities.

**Properties:**
- `GateName`: Gate identifier (e.g., A1, B2, C3)
- `SupportsDDJB`: Whether gate supports DDJB requests
- `SupportsCFFT`: Whether gate supports CFFT requests
- `SupportsLWTT`: Whether gate supports LWTT requests
- `Flight`: Currently assigned flight (if any)

## 💰 Fee Structure

### Base Fees
- **Arriving Flight**: $500
- **Departing Flight**: $800
- **Boarding Gate Base Fee**: $300 (for departing flights only)

### Special Request Fees
- **DDJB**: +$300
- **CFFT**: +$150
- **LWTT**: +$500

### Discount Rules
1. **High Volume Discount**: 3% off total bill for airlines with more than 5 flights
2. **Off-Peak Discount**: $110 per flight departing/arriving before 11:00 AM or after 9:00 PM
3. **Custom Origin Discount**: $50 per flight from Dubai (DXB), Bangkok (BKK), or Tokyo (NRT)

## 📊 Data Files

### airlines.csv
Contains airline information:
- Airline Name
- Airline Code

### boardinggates.csv
Contains boarding gate configuration:
- Boarding Gate Name
- DDJB Support (True/False)
- CFFT Support (True/False)
- LWTT Support (True/False)

### flights.csv
Contains flight information:
- Flight Number
- Origin
- Destination
- Expected Departure/Arrival Time
- Special Request Code (DDJB/CFFT/LWTT or empty)

## 🚀 Getting Started

### Prerequisites
- .NET 8.0 SDK or later
- Visual Studio 2022 or Visual Studio Code

### Installation

1. Clone the repository:
```bash
git clone https://github.com/xanyeooooo/PRG2_Assignment.git
```

2. Navigate to the project directory:
```bash
cd PRG2_Assignment/PRG2_Assignment
```

3. Build the project:
```bash
dotnet build
```

4. Run the application:
```bash
dotnet run
```
