# Scheduled Notifications Service

The **Scheduled Notifications Service** automates the process of sending notifications based on user-defined schedules. Built with **Node.js**, **Express.js**, and **MongoDB**, this service provides flexible scheduling options for daily, weekly, monthly, and custom intervals. It utilizes **Moment.js** for precise scheduling and **Firebase Cloud Messaging (FCM)** for delivering notifications.

## 🚀 Features

- **One-Time and Recurring Notifications**: Supports one-time notifications or recurring schedules (daily, weekly, monthly, or custom intervals).
- **Flexible Time Zone Support**: Users can specify time zones, allowing notifications to be scheduled and sent accurately across different regions.
- **Dynamic Scheduling**: Notifications can be set to repeat based on user preferences, with custom intervals available.
- **End Date Tracking**: Notifications will automatically stop sending after the specified end date.
- **Error Handling**: Robust error handling ensures that any failed notifications are logged and can be retried if necessary.
- **Job Queuing**: Uses **BullMQ** to manage and process notification jobs efficiently, ensuring reliability in sending notifications.
- **Data Persistence**: Utilizes **Redis** to store job and notification statuses, providing a fast, in-memory data structure store.
- **Admin Dashboard**: Features a user-friendly interface for managing notifications, viewing logs, and tracking the status of sent notifications.

## 🛠️ Technology Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB for storing notification schedules and status
- **Job Queue**: BullMQ for processing notification jobs
- **Caching**: Redis for managing job statuses and performance
- **Scheduling**: Node-Cron and Moment.js to handle time-based scheduling and conversions
- **Notifications**: Firebase Cloud Messaging (FCM) for sending push notifications to clients

## 📋 API Endpoints

### **for more detailed and example requests API documentation please visit: https://documenter.getpostman.com/view/33627575/2sAY4sijWQ

## 🔄 Notification Scheduling Logic

The Cron job runs every second to check for notifications that are due to be sent:

1. **Fetch Notifications**: Retrieves all pending notifications from the database.
2. **Check Schedule**: For each notification, it checks if the scheduled time matches the current UTC time.
3. **Send Notification**: If due, it sends the notification using FCM.
4. **Repeat Logic**: If the notification has a repeat type, it calculates the next scheduled time using the `nextRepeat` function and updates the schedule in the database.
5. **End Date**: If an end date is provided and reached, the notification status is marked as "sent," stopping further recurrence.

### `nextRepeat` Function

The `nextRepeat` function calculates the next occurrence based on the repeat type:
- **Daily**: Adds 1 day
- **Weekly**: Adds 1 week
- **Monthly**: Adds 1 month
- **Custom**: Adds a specified interval in days

## 🚀 Getting Started

### Prerequisites

- Node.js
- MongoDB
- Redis

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Ahmed-Khalil-96/scheduled-notifications.git
   cd scheduled-notifications-service

2. Install dependencies:
   ```bash
    npm install

3. Set up your environment variables:
   Create a .env file in the root directory and add your configuration settings.

4. Start the server: npm start

### 📞 Contact
For inquiries or contributions, please contact Ahmed Khalil at ahmed.elabassiry96@gmail.com.


### Changes Made:

1. **Features**: Added details about **Job Queuing** with **BullMQ**, **Data Persistence** with **Redis**, and an **Admin Dashboard**.
2. **Technology Stack**: Included Redis and BullMQ in the tech stack.
3. **Installation Prerequisites**: Mentioned Redis as a requirement for running the application.
