import os
from slack_sdk import WebClient
from slack_sdk.errors import SlackApiError


client = WebClient(token=os.environ["SLACK_BOT_TOKEN"])


def set_dnd_status(duration):
    try:
        response = client.users_profile_set(
            profile={
                "status_text": "In a work session",
                "status_emoji": ":hourglass_flowing_sand:",
                "status_expiration": duration
            }
        )
        return response
    except SlackApiError as e:
        print("Error setting DND status: {}".format(e))

def send_message(channel_id, message):
    try:
        response = client.chat_postMessage(
            channel=channel_id,
            text=message
        )
        return response
    except SlackApiError as e:
        print("Wait for the end of work session to send your message: {}".format(e))

def handle_work_command(duration):
    set_dnd_status(duration)
    send_message(user_id, "You are now in a work session. Focus is power!")
    send_message(channel_id, "<@{}> is now in a work session. Please do not disturb until the communication window begins.".format(user_id))

def handle_comm_command(duration):
    send_message(user_id, "You are now in a communication window. You can now send and receive messages.")
    send_message(channel_id, "<@{}> is now available for communication. Feel free to send messages.".format(user_id))

def handle_command(command, duration):
    if command == "/work":
        handle_work_command(duration)
    elif command == "/comm":
        handle_comm_command(duration)
    else:
        send_message(user_id, "Invalid command. Please use /work or /comm.")

def main(request):
    command = request.form["command"]
    duration = request.form["text"]
    user_id = request.form["user_id"]
    channel_id = request.form["channel_id"]

    handle_command(command, duration)
