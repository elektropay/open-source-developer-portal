---
layout: twoColumn
section: guides
type: iOS Developer's Guide
guide: 
    name: ios-guide
    step: 04-01-fetch-existing-data-plugs-applications
title: "- Listing Data Plugs and Applications"
description: Guide to Listing Data Plugs Applications on the HAT on the iOS platform
---
# Fetch Data Plugs and Applications

`HAT for iOS` provides an API call for you to fetch all the available `Data Plugs`:

```javascriptnoselect
HATExternalAppsService.getExternalApps(
            userToken: userToken,
            userDomain: userDomain,
            completion: availablePlugsReceived,
            failCallBack: errorRetrievingDataPlugs)
```

As you would have probably noticed, the function name is `getExternalApps`. `Applications` and `Data Plugs` are not only represented by the same structure but they have the same API as well.

* `userToken` is the user's token in order to authenticate with the `HAT`.
* `userDomain` is the user's `HAT address` in order to form the url to fetch the `Data Plugs`.
* `completion` is a callback that is called when the request was successful. It has type of `@escaping (([HATApplicationObject], String?) -> Void)`. The first parameter is an array of `HATApplicationObject`. This is the structure of `Data Plugs` and `Applications`. More on that in the next section. This array contains all the `Data Plugs` **and** `Applications` on the `HAT`. The second parameter is an optional `String`, the refreshed user token that the `HAT` returns.
* `failCallBack` is callback that is called when the request has failed. They type of the function is `@escaping ((HATTableError) -> Void)`. `HATTableError` is custom object describing the errors that have occurred during the querying of the tables in the database.

A successful response will have `statusCode` 200 and look like this:

```jsonnoselect
[
    {
        "application": {
            "id": "hatapp",
            "kind": {
                "url": "https://rumpel.hubofallthings.com",
                "iosUrl": "https://itunes.apple.com/app/id1303181222?mt=8",
                "kind": "App"
            },
            "info": {
                "version": "1.2.5",
                "updateNotes": {
                    "header": "We’ve made some improvements to the user experience and made clear your legal rights over your data so that you can access new services on your HAT app. Please accept our updated [terms of service](https://hatdex.org/terms-of-service-hat-owner-agreement) and [privacy policy](https://hatdex.org/privacy-notice-hat-owner-services-and-hat-accounts) to continue using HAT.",
                    "notes": [
                        "We made clear the difference between “your data” in your HAT microserver and “HATDeX account data” which we need to create your HAT microserver",
                        "We made clear the relationship between HAT permissions and instructions that you control within the HAT versus HATDeX platform services and third party services that others control (when you give permission) to help you easily view, manage and organise the data within the HAT",
                        "We made clear the way data debits and data plugs operate based on the permissions and instructions you control and the services we control to execute your instructions",
                        "We updated the way we use your information for HATDeX account data in accordance with GDPR",
                        "We updated the way apps, plugs and tools are rated to give HAT owners full transparency on services and apps \"Powered by HAT\". Find more info [here](https://www.hatcommunity.org/hat-dex-rating)"
                    ]
                },
                "published": true,
                "name": "HAT App",
                "headline": "The HAT Dashboard",
                "description": {
                    "text": "\n Your digital life is made up of hundreds of day to day interactions on the Internet: liking and sharing content, booking train tickets, tracking your activity. It's time to see them all come together, in one place, so you can benefit from analysis, insights and self-discovery on your personal data.\n\n CONNECT DATA PLUGS\n Link your Twitter, Facebook, Spotify, FitBit, Google Calendar and iPhone GPS locations to your HAT, and pull in all that data in real time. Your data is kept in an entirely private space, owned by you – we don't see it, third parties don't see it, no-one sees it but you.\n\n YOUR DIGITAL LIFE\n View your data in a live feed where you can experience and engage with it as it arrives into your HAT. Facebook posts, workouts recorded by FitBit, photos you've shared – see it all in one integrated feed. Search your data by date range to know exactly where you were and what digital actions you took at any given time.\n\n PUBLIC PROFILE\n Save your personal information privately, and customise exactly which parts you want to share publicly on your Personal HAT Address – your own public URL. Think of it as the front door to your HAT, and use it to display the information you'd like.\n\n ME, MYSELF AND AI\n We will be releasing the Smart HAT Engine (SHE) soon – this engine on your HAT will enable you to subscribe to different types of analytics and machine learning functions to give you daily insights and help you make better decisions with your data, completely in your private space. Start claiming your data for yourself so that you can better use AI in your life.\n\n One HAT, so many possibilities: our HAT Community of startups and app makers is creating a new generation of Internet applications sitting on your HAT. With all the data in the account, you can donate your data to research, spend it, match it and exchange it for services. Join the community to be part of the movement to change the Internet at https://hatcommunity.org\n\n          ",
                    "markdown": "\n Your digital life is made up of hundreds of day to day interactions on the Internet: liking and sharing content, booking train tickets, tracking your activity. It's time to see them all come together, in one place, so you can benefit from analysis, insights and self-discovery on your personal data.\n\n ### Connect Data Plugs\n\n Link your Twitter, Facebook, Spotify, FitBit, Google Calendar and iPhone GPS locations to your HAT, and pull in all that data in real time. Your data is kept in an entirely private space, owned by you – we don't see it, third parties don't see it, no-one sees it but you.\n\n ### Your Digital Life\n\n View your data in a live feed where you can experience and engage with it as it arrives into your HAT. Facebook posts, workouts recorded by FitBit, photos you've shared – see it all in one integrated feed. Search your data by date range to know exactly where you were and what digital actions you took at any given time.\n\n ### Public Profile\n\n Save your personal information privately, and customise exactly which parts you want to share publicly on your Personal HAT Address – your own public URL. Think of it as the front door to your HAT, and use it to display the information you'd like.\n\n ### Me, Myself and AI\n\n We will be releasing the Smart HAT Engine (SHE) soon – this engine on your HAT will enable you to subscribe to different types of analytics and machine learning functions to give you daily insights and help you make better decisions with your data, completely in your private space. Start claiming your data for yourself so that you can better use AI in your life.\n\n One HAT, so many possibilities: Our HAT Community of startups and app makers is creating a new generation of Internet applications sitting on your HAT. With all the data in the account, you can donate your data to research, spend it, match it and exchange it for services. Join the community to be part of the movement to change the Internet at https://hatcommunity.org\n                                ",
                    "html": "\n <p>Your digital life is made up of hundreds of day to day interactions on the Internet: liking and sharing content, booking train tickets, tracking your activity. It's time to see them all come together, in one place, so you can benefit from analysis, insights and self-discovery on your personal data.</p>\n\n <h3>Connect Data Plugs</h3>\n\n <p>Link your Twitter, Facebook, Spotify, FitBit, Google Calendar and iPhone GPS locations to your HAT, and pull in all that data in real time. Your data is kept in an entirely private space, owned by you – we don't see it, third parties don't see it, no-one sees it but you.</p>\n\n <h3>Your Digital Life</h3>\n\n <p>View your data in a live feed where you can experience and engage with it as it arrives into your HAT. Facebook posts, workouts recorded by FitBit, photos you've shared – see it all in one integrated feed. Search your data by date range to know exactly where you were and what digital actions you took at any given time.</p>\n\n <h3>Public Profile</h3>\n\n <p>Save your personal information privately, and customise exactly which parts you want to share publicly on your Personal HAT Address – your own public URL. Think of it as the front door to your HAT, and use it to display the information you'd like.</p>\n\n <h3>Me, Myself and AI</h3>\n\n <p>We will be releasing the Smart HAT Engine (SHE) soon – this engine on your HAT will enable you to subscribe to different types of analytics and machine learning functions to give you daily insights and help you make better decisions with your data, completely in your private space. Start claiming your data for yourself so that you can better use AI in your life.</p>\n\n <p>One HAT, so many possibilities: Our HAT Community of startups and app makers is creating a new generation of Internet applications sitting on your HAT. With all the data in the account, you can donate your data to research, spend it, match it and exchange it for services. Join the community to be part of the movement to change the Internet at https://hatcommunity.org</p>\n                                                       "
                },
                "termsUrl": "https://hatdex.org/terms-of-service-hat-owner-agreement-2018-10-01",
                "dataUsePurpose": "The HAT App only uses your data to display it back to you. It does not share your data with any third-parties or store it outside of your personal HAT.",
                "supportContact": "contact@hatdex.org",
                "rating": {
                    "score": "Z***"
                },
                "dataPreview": [
                    {
                        "source": "she",
                        "date": {
                            "iso": "2018-10-31T08:54:26.303Z",
                            "unix": 1540976066
                        },
                        "types": [
                            "note"
                        ],
                        "title": {
                            "text": "HAT Private Micro-server created"
                        },
                        "content": {
                            "text": "Digital Citizenship on the Internet is about the freedom of having our own persona(s) with the data we are able to claim, control and share. You now have a HAT micro-server to do that. Congratulations!"
                        }
                    }
                ],
                "graphics": {
                    "banner": {
                        "normal": ""
                    },
                    "logo": {
                        "normal": "https://static1.squarespace.com/static/5a71ebc8b1ffb68777ca627a/t/5acb4a166d2a73d3a00a10c6/1523272220659/HATAppsstore-rounded.png?format=300w"
                    },
                    "screenshots": [
                        {
                            "normal": "https://is1-ssl.mzstatic.com/image/thumb/Purple116/v4/cb/01/56/cb0156b7-0cb6-128c-b1ec-fc3c7b31eb87/mzl.xfaethox.png/300x0w.jpg",
                            "large": "https://is5-ssl.mzstatic.com/image/thumb/Purple128/v4/ac/a2/6b/aca26bb8-39dd-1cd9-159d-d37012ffbfeb/mzl.jiaxtegz.png/643x0w.jpg"
                        },
                        {
                            "normal": "https://is4-ssl.mzstatic.com/image/thumb/Purple118/v4/26/b7/0f/26b70ffa-d9bc-2520-582b-b9a436eb00f5/pr_source.png/300x0w.jpg",
                            "large": "https://is4-ssl.mzstatic.com/image/thumb/Purple128/v4/9b/2f/68/9b2f6853-ce11-a189-ae41-445e8e7b3248/mzl.fkcehkpp.png/643x0w.jpg"
                        },
                        {
                            "normal": "https://is4-ssl.mzstatic.com/image/thumb/Purple128/v4/10/df/8f/10df8fae-b2b7-0c93-c530-d6338b1e6bc8/pr_source.png/300x0w.jpg",
                            "large": "https://is4-ssl.mzstatic.com/image/thumb/Purple118/v4/28/de/7a/28de7aeb-54ed-6692-a63a-8102703361e2/pr_source.png/643x0w.png"
                        },
                        {
                            "normal": "https://is5-ssl.mzstatic.com/image/thumb/Purple128/v4/15/94/30/159430c6-99fc-ee9f-72aa-d46d8436d76c/mzl.dvmpzlje.png/300x0w.jpg",
                            "large": "https://is2-ssl.mzstatic.com/image/thumb/Purple118/v4/11/df/40/11df4050-582a-7598-fe02-b4421a4be818/pr_source.png/643x0w.png"
                        }
                    ]
                }
            },
            "developer": {
                "id": "hatdex",
                "name": "HAT Data Exchange Ltd",
                "url": "https://hatdex.org",
                "country": "United Kingdom"
            },
            "permissions": {
                "rolesGranted": [
                    {
                        "role": "owner"
                    },
                    {
                        "role": "applicationlist"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "hatappstaging"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "notables"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "twitter"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "facebook"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "fitbit"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "spotify"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "instagram"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "monzo"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "fitbit"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "google-calendar"
                    },
                    {
                        "role": "applicationmanage",
                        "detail": "starling"
                    }
                ]
            },
            "setup": {
                "url": "https://rumpel.hubofallthings.com",
                "iosUrl": "hatapp://hatapphost",
                "kind": "External"
            },
            "status": {
                "compatibility": "1.2.5",
                "dataPreviewEndpoint": "she/feed",
                "recentDataCheckEndpoint": "rumpel/locations/ios",
                "versionReleaseDate": "2018-07-23T12:00:00.000Z",
                "kind": "Internal"
            }
        },
        "setup": true,
        "enabled": true,
        "active": true,
        "needsUpdating": true,
        "mostRecentData": "2018-11-12T08:27:57.609Z"
    }
  ]
```

* `application` holds the most parts of the structure. It consists of the following 7 values:
  1. `id` in the `application` part of the JSON is the `id` of the `Data Plug` in the `HAT`.
  2. `kind` in the `application` part of the JSON has 4 values holding the various urls and the type of the `Data Plug`:
    1. `url` is the url of the `Data Plug` or `Application` to use in web
    2. `iosUrl` is the iTunes url of the `Application` in the `App Store`. It's ***optional*** and only there for `Application` type
    3. `androidUrl` is the Play Store url of the `Application` in the `Play Store`. It's ***optional*** and only there for `Application` type
    4. `kind` is the kind. As we mentioned earlier `Data Plug` and `Application` is represented by the same structure and use the same APIs. Therefore the `kind` can be `App` or `DataPlug`. When for example you want only the `Applications` then simply you are going to filter the array based on the `kind`.
  3. `info` in the `application` part of the JSON has 12 values:
    1. `version` is the version number of the app in the `HAT`. This may be different than the version number of the `Application` in the `App Store` or `Play Store`
    2. `updateNotes` is essentially the release notes for the latest version. It is formed by the `header`, the title of the release notes, and the `notes` an array of `String` to easily show the notes as an unordered list.
    3. `published` indicates if the app is published or not. It can be that the app is not yet published, so it's not yet live, and it's testing, beta, app
    4. `name` is the official name of the app
    5. `headline` is the headline or subtitle of the app. It can be placed underneath the name for example to provide more context for the app if needed.
    6. `description` allows you to describe your app better with a longer text. Also it has support for different formats of text, `text`, `markdown` and `html`. `markdown` and `html` are ***optional***.
    7. `termsUrl` is a `URL` of the terms and conditions. Users must be able to read them if they wish
    8. `dataUsePurpose` is a text explaining why and how the app will use the data
    9. `supportContact` a support email. Users will use this email to contact you.
    10. `rating` is an ***optional*** object formed by `score` which describes the permissions and the data use using a letter based scoring system. You can read more [here](https://www.hatcommunity.org/hat-dex-rating)
    11. `dataPreview` is actually an array of `SheFeed` structures. This is used to preview items, if any, instead of making another network request to fetch those items. The array can be empty.
    12. `graphics` is a structure formed by 3 values:
      1. `banner` is the `URL` of the banner image
      2. `logo` is the `URL` of the app logo image
      3. `screenshots` is the `URL` of the app's screenshots used to showcase what this app offers.
      All of the above 3 values use the same structure. `HAT` images can be categorized as `small`, `normal`, `large` and `xlarge`. Except `normal` all are ***optional*** values.
  4. `developer` consists of some basic info about the developer. This includes: `id`, `name`, `url` and `country`
  5. `permissions` includes 3 values:
    1. `rolesGranted` which is an array of `role` and `detail`, ***optional***, describing the roles granted in the `Application`
    2. `dataRetrieved` which is a type of `DataOfferRequiredDataDefinitionObjectV2`. It describes the data that the `Application` will retrieve. ***optional***:
      1. `rolling` describes if the data have a rolling start date
      2. `bundle` You can read more about it [here](03-01-fetch-existing-data-debits.html)
      3. `startDate` the start date of the `bundle`. ***optional***
      4. `endDate` the end date of the `bundle`. ***optional***
    3. `dataRequired` which is a type of `HATExternalAppsDataRequiredObject`. You can read more about it [here](03-01-fetch-existing-data-debits.html). ***optional***
  6. `setup` encapsulates all the urls that the `Application` needs in order to setup. The structure is the same as `kind` but the url's can be different
  7. `status` provides some info about the status of the application:
    1. `compatibility` The last version that is compatible with the current one
    2. `versionReleaseDate` The date, in `ISO` format, of the latest release
    3. `kind` the kind of the release. It can be either `Internal` or `External`
    4. `recentDataCheckEndpoint` is a `URL` pointing on the most recent data point. ***optional***
    5. `statusUrl` is a `URL` to check the status of the `Application` or `Data Plug`. ***optional***
    6. `expectedStatus` the expected status number. ***optional***
    7. `dataPreviewEndpoint` a `URL` pointing to the actual data on the `HAT` do show them as a preview. ***optional***
* `setup` Boolean value indicating if this app has been setup successfully
* `enabled` Boolean value indicating if this app has been enabled successfully
* `active` Boolean value indicating if this app is currently active or not
* `needsUpdating` Boolean value indicating if this app needs updating. An `Application` may need an update in case the terms have changed or a new version has been released.

A request that has failed will look like this:

```jsonnoselect
{
  "error": "Not Authenticated",
  "message": "Not Authenticated"
}
```

* `error` is the error that has occurred.
* `message` a more descriptive message about the `error` that has occurred

<nav class="pager-nav">
<a href="" style="display:none;"></a>
<a href="04-02-setup-data-plugs-applications.html">Next Step: Setting Up Data Plugs and Applications</a>
</nav>
