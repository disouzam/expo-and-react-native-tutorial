# About
Tutorial on how to use React Native and Expo - based in https://docs.expo.dev/tutorial/introduction/

## Git ignore template

[Expo.gitignore](https://github.com/disouzam/gitignore/blob/main/community/JavaScript/Expo.gitignore)

# Chapter 1: Create your first app

```bash
npx create-expo-app@latest StickerSmash 
cd StickerSmash
```

```bash
mv assets/images/sticker-smash-assets/images/* assets/images
rm -rf assets/images/sticker-smash-assets/images
rm -rf assets/images/sticker-smash-assets
```

Resetting project

```bash
npm run reset-project
# Then select option to move files to app-example folder instead of deleting files
```

Run the app on mobile and web

```bash
npx expo start
```

# Chapter 2: Add navigation

Added an about screen

```bash
# [Add a new screen to the stack](https://docs.expo.dev/tutorial/add-navigation/#add-a-new-screen-to-the-stack)
echo """import { Text, View, StyleSheet } from 'react-native';

export default function AboutScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>About screen</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    color: '#fff',
  },
});
""" > app/about.tsx
```


Add a not-found route

```bash
echo """import { View, StyleSheet } from 'react-native';
import { Link, Stack } from 'expo-router';

export default function NotFoundScreen() {
  return (
    <>
      <Stack.Screen options={{ title: 'Oops! Not Found' }} />
      <View style={styles.container}>
        <Link href='/' style={styles.button}>
          Go back to Home screen!
        </Link>
      </View>
    </>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#25292e',
    justifyContent: 'center',
    alignItems: 'center',
  },

  button: {
    fontSize: 20,
    textDecorationLine: 'underline',
    color: '#fff',
  },
});
""" > app/+not-found.tsx
```