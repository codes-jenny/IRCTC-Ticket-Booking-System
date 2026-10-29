# IRCTC Ticket Booking System

A command-line train ticket booking application in Java, modelled on IRCTC. Users can sign up, log in, search trains between stations, book seats and cancel bookings. Data is stored in local JSON files.

## Features

- **User sign-up and login**, with passwords stored as hashes rather than plain text
- **Train search** by source and destination station
- **Seat booking** on a chosen train, with seat availability tracked per train
- **Booking history**: view all tickets booked by the logged-in user
- **Ticket cancellation** by ticket ID
- **JSON persistence**: users, trains and tickets are saved to local JSON files, so data survives between runs

## Design

The app follows object-oriented design, with each domain concept modelled as its own class:

| Layer | Classes | Responsibility |
|---|---|---|
| Entities | `User`, `Train`, `Ticket` | Domain models holding user details, train routes and seats, and booking records |
| Services | `UserBookingService`, `TrainService` | Business logic for login, sign-up, search, booking and cancellation |
| Utilities | `UserServiceUtil` | Helpers such as password hashing and checking |
| Storage | `localDb/users.json`, `localDb/trains.json` | JSON files read and written through Jackson's `ObjectMapper` |

## Tech Stack

- **Java**
- **Gradle** for build and dependency management
- **Jackson** for JSON serialization and deserialization

## Project Structure

```
app/
└── src/main/java/ticket/booking/
    ├── App.java              # Entry point and command-line menu
    ├── entities/             # User, Train, Ticket
    ├── services/             # UserBookingService, TrainService
    ├── util/                 # UserServiceUtil
    └── localDb/              # users.json, trains.json
```

## How to Run

Requires **Java 17+**. Gradle is included through the wrapper, so it doesn't need to be installed separately.

```bash
git clone https://github.com/codes-jenny/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME
./gradlew run          # on Windows: gradlew.bat run
```

Then follow the menu in the terminal:

```
1. Sign up
2. Login
3. Fetch bookings
4. Search trains
5. Book a seat
6. Cancel my booking
7. Exit
```

## Acknowledgements

Built while following the [Java ticket booking tutorial series](https://www.youtube.com/playlist?list=PL7CBVLpg0zqeJTCCuU99RW1TMn8_Ii15n) by Lovepreet Singh.
