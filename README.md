# Tournament Bracket Predictor

A React Native mobile app that allows sports fans to predict the outcomes of three major single-elimination tournaments right from their phone: the UEFA Champions League, the FIFA World Cup, and the NCAA Men's or Women's Division I Basketball Tournament (March Madness).

## About the Project

The idea came from combining two things that I love, which are sports and the development skills I picked up over the semester. Millions of people around the world enjoy predicting who will win each game in these big tournaments, but their picks are usually scattered across paper brackets, group texts, and different websites. The Tournament Bracket Predictor gives those fans one single place on their phone to record every prediction they make.

Because the user types in the teams themselves, the app stays flexible and can be used again every season. When new teams qualify next year, the user just clears the old list and types in the new one. Nothing has to be updated in the code.

## What the App Does

The app walks the user through three simple steps for any tournament they pick. First, the user chooses one of the three tournaments from the home screen. Each tournament has its own logo and its own saved memory, so picks made in one tournament will never overwrite or affect picks made in another. A user can even fill out all three brackets at the same time and switch between them whenever they want.

After choosing a tournament, the user lands on a menu screen with three clear buttons. The first button takes them to the team setup screen, the second takes them to the bracket itself, and the third takes them to a summary of everything they have predicted so far. A red "Switch Tournament" button at the bottom lets the user jump back to the home screen and pick a different tournament at any time.

On the team setup screen, the user types in a team name and pastes a link to that team's logo image, then taps "Add Team" to save it. Each team that gets added shows up in a numbered list along with its logo. Tapping any team in the list removes it. The app keeps adding teams until 16 have been registered, at which point the user can move on to the bracket. The list of teams is saved on the phone, so closing the app does not erase the user's work.

The bracket screen is where the predictions actually happen. The app automatically pairs the 16 teams into 8 "Round of 16" matches based on the order they were added. The user taps the team they think will win each match, and the winner moves on to the next round. The same process happens for the Quarterfinals, the Semifinals, and the Final. A progress bar at the top shows how many of the 15 total picks have been made. If the user changes their mind about a Round of 16 winner, the app is smart enough to automatically erase any later picks that depended on that original choice, so the bracket can never end up in an impossible state. Once the champion is chosen, a golden box appears at the bottom of the screen to celebrate the predicted winner.

The summary screen, reached by tapping "View My Predictions" on the menu, shows every pick the user has made in a clean and organized list. The predicted champion appears at the top in the same golden box, followed by sections for the Round of 16 winners, the Quarterfinal winners, and the Semifinal winners. Each pick is shown with the team's logo next to its name. A red "Clear Predictions" button at the bottom lets the user wipe everything and start over with fresh picks.

## How the App Is Built

The app is written in React Native using the Expo framework, which is what makes it possible to run on a real iPhone or Android phone. Navigation between screens is handled by React Navigation's stack navigator, meaning each new screen slides in on top of the previous one and the user can tap "Back" at the top to return.

All of the user's data, including the team lists and the bracket picks, is saved on the phone itself using AsyncStorage. AsyncStorage is basically a simple key-value database that lives on the device, so the user's predictions stay there even when the phone is turned off or the app is closed. Each tournament uses its own pair of storage keys, which is what allows the three brackets to stay completely separate from one another.

The screens themselves are organized into five main components. The Home screen lists the three tournaments to pick from. The Menu screen shows the options for whichever tournament was selected. The Setup screen handles adding and removing teams. The Bracket screen displays the full bracket and tracks which team won each match. The Summary screen lays out every pick the user has made in a readable format. A smaller helper component called MatchBox is reused throughout the bracket to draw each individual matchup, which keeps the code clean and consistent.

## Getting Started

To run this app on your own machine, you will need Node.js installed along with the Expo CLI. After cloning the repository, run `npm install` inside the project folder to download all of the dependencies, and then run `npx expo start` to launch the development server. From there, you can open the app on your phone by scanning the QR code with the Expo Go app, or you can run it in an iOS or Android simulator on your computer.

The main dependencies are React Native itself, `@react-navigation/native` and `@react-navigation/stack` for moving between screens, `react-native-safe-area-context` for handling the notch and home bar on modern phones, and `@react-native-async-storage/async-storage` for saving data on the device.

## Possible Improvements

There are a few features I would like to add in the future to make the app even better. The biggest one would be connecting to a real sports data service so that team names and logos could be pulled in automatically, instead of asking the user to type them in and paste an image link. This would save a lot of setup time and would make the app feel more polished.

I would also love to add a scoring system that compares the user's predictions against the actual results once the games have been played, and gives the user points for each correct pick. This would add a fun gamification element and would let users compete with their family and friends. A leaderboard page could show everyone's running score across the season. Beyond that, I would like to build a full database so that users can keep their brackets from past seasons, look back at how they did, and share their picks with friends.

## Author

Edwin Li
