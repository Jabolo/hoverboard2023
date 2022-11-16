## Notifications

There are two types of [push notifications](https://firebase.google.com/products/cloud-messaging) supported.

Browsers that support [`Navigator.permissions`](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/permissions) and are supported by [Firebase Messaging](https://firebase.google.com/docs/web/environments-js-sdk).

### My Schedule notifications

A few minutes before a sessions starts, attendees can get reminder notifications. These are sent automatically by [`schedule-notifications.ts`](functions/src/schedule-notifications.ts).

To get a notification an attendee has to:

1. Be authenticated
1. Have enabled "My Schedule notifications"
1. Have bookmarked the session that is about to start

### General notifications

General notifications are sent to everyone (authenticated and anonymous) who has enabled "General notifications". These are sent manually by conference organizers.

To send a "General notification":

1. Got to the [project's Firestore page](https://console.firebase.google.com/u/0/project/_/firestore/data/)
1. "Start collection" with the ID `notifications`
1. On the document creation page enter the following three fields
   - `title`: `Announcing GDG DevFest Ukraine 2017`
   - `body`: `It is official. GDG DevFest Ukraine 2017 is going to take place in Lviv, on October 13-14.`
   - `path`: `/blog/dfua17-announced`
1. Save

General notifications are sent by the sendGeneralNotification cloud function that is trigger by adding documents on /notifications/{timestamp} in firestore. You basically create a new document there with:

regardless the timestamp these are send immediately

timestamp like: 2022-11-16T18:25:12
{
"title": "Notification Title",

"body": "Notification Body Message",

"click_action": "https://<your url here>/

}

enable: https://console.cloud.google.com/apis/api/googlecloudmessaging.googleapis.com

enable: https://console.cloud.google.com/apis/api/firebaseinappmessaging.googleapis.com
