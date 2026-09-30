# Real-Time Cloud Event RSVP Tracker

A cloud-based event management and RSVP platform that enables organizers to create and manage events while attendees can register, RSVP, and receive real-time updates.

## Live Application

Frontend:
https://real-time-cloud-event-rsvp-tracker-1-dsxf.onrender.com

Backend API:
https://real-time-cloud-event-rsvp-tracker-e6qb.onrender.com

API Documentation:
https://real-time-cloud-event-rsvp-tracker-e6qb.onrender.com/docs

## Project Overview

The Real-Time Cloud Event RSVP Tracker is a full-stack cloud computing project designed to demonstrate how modern web applications can use cloud databases, REST APIs, authentication, WebSockets, and cloud deployment.

The system supports two major roles:

- Organizer
- Attendee

Organizers can create and manage events, while attendees can view events and submit RSVP responses.

The platform also provides real-time RSVP updates using WebSockets, allowing organizer dashboards to update without manually refreshing the page.

## Key Features

### Authentication and Authorization

- User registration and login
- JWT-based authentication
- Role-based access control
- Organizer and attendee roles

### Event Management

- Create events
- View available events
- Event date and time management
- Event location
- Maximum event capacity
- Event status management

### RSVP Management

- GOING
- MAYBE
- NOT_GOING
- RSVP status tracking
- Event capacity tracking
- Automatic attendee count updates

### Real-Time Communication

The application uses WebSockets to provide real-time RSVP updates.

When an attendee changes their RSVP status:

1. The backend processes the RSVP.
2. The updated attendee counts are calculated.
3. A WebSocket event is broadcast to connected clients.
4. The organizer dashboard receives the update.
5. The dashboard updates without requiring a page refresh.

## Technology Stack

### Frontend

- React
- Vite
- JavaScript
- HTML
- CSS

### Backend

- Python
- FastAPI
- SQLAlchemy
- Pydantic
- JWT Authentication
- WebSockets

### Database

- PostgreSQL for cloud deployment
- SQLite for local development

### Deployment

- GitHub
- Render
- Render PostgreSQL
- Docker

## Architecture

```text
                    ┌──────────────────────┐
                    │      User / Browser  │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    React Frontend    │
                    │       Vite           │
                    └──────────┬───────────┘
                               │
                    REST API / WebSocket
                               │
                               ▼
                    ┌──────────────────────┐
                    │    FastAPI Backend   │
                    │ Authentication       │
                    │ Event Management      │
                    │ RSVP Management       │
                    │ WebSocket Manager     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ PostgreSQL Database  │
                    │      Cloud DB        │
                    └──────────────────────┘