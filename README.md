                                        # Django Chat Application



This is a simple real-time chat application built with Django and Channels, providing WebSocket support for real-time communication between users.

## Features

- **User Authentication**: Users can sign up and log in to the chat application.
- **WebSocket Support**: Real-time messaging with WebSocket, allowing users to send and receive messages instantly.
- **Message History**: Messages are stored in the database and can be retrieved when users view their chats.
- **User List**: Displays all registered users for the logged-in user to initiate chats.

## Installation

### Prerequisites
- Python 3.8+
- Django 3.x or higher
- Channels 3.x
- Redis (for WebSocket support)

### Steps to Install

1. **Clone the repository**:

    ```bash
    git clone https://github.com/yourusername/django-chat-app.git
    cd django-chat-app
    ```

2. **Create and activate a virtual environment**:

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use venv\Scripts\activate
    ```

3. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up the database**:

    ```bash
    python manage.py migrate
    ```

5. **Start the development server**:

    ```bash
    python manage.py runserver
    ```

6. **Open the app in a browser**:

    Go to `http://127.0.0.1:8000` to access the chat app.

## Configuration

1. **Add the necessary apps to `INSTALLED_APPS` in `settings.py`**:

    ```python
    INSTALLED_APPS = [
        ...
        'channels',
        'chat',  # Your app for the chat
    ]
    ```

2. **Configure `ASGI_APPLICATION` for WebSocket**:

    ```python
    ASGI_APPLICATION = 'chat_project.asgi.application'
    ```

3. **Set up Redis for WebSocket communication**.

    Redis is required for Django Channels to work efficiently.

    ```bash
    pip install channels_redis
    ```

    In `settings.py`, add the following configuration:

    ```python
    CHANNEL_LAYERS = {
        'default': {
            'BACKEND': 'channels_redis.core.RedisChannelLayer',
            'CONFIG': {
                "hosts": [('127.0.0.1', 6379)],
            },
        },
    }
    ```

## Usage

- **Sign Up**: Users can register for an account.
- **Login**: Users can log in to access the chat application.
- **Chat**: Users can view the list of other users, initiate conversations, and send messages.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
