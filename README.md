# Expo Linking.getInitialURL() returns null on Android intermittently

This repository demonstrates a bug where Expo's `Linking.getInitialURL()` method on Android may return `null` even when the app was launched from a deep link.  The issue is intermittent and difficult to consistently reproduce, but the provided example showcases the problem and a possible workaround.

## Problem

The core issue lies in the unreliability of `Linking.getInitialURL()` when called immediately after the app starts, particularly when launched directly via a deep link.  The method may return `null` despite a valid deep link being passed. This can prevent the app from properly handling the link and processing the associated data.

## Solution

The provided solution uses a combination of `Linking.addEventListener` and `Linking.getInitialURL` to ensure that the deep link is captured reliably.  The event listener handles cases where the URL isn't immediately available and provides a robust method to catch the deep link, even after a slight delay.