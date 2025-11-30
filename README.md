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

Create "(tabs)" subdirectory and adjust files accordingly

```bash
mkdir "app/(tabs)" # Assuming you are in StickerSmash folder and not in repo's root folder. Otherwise, do `cd StickerSmash` first
mv app/index.tsx "app/(tabs)"
mv app/about.tsx "app/(tabs)"
cp app/_layout.tsx "app/(tabs)"


echo """import { Stack } from 'expo-router';

export default function RootLayout() {
  return (
    <Stack>
      <Stack.Screen name='(tabs)' options={{ headerShown: false }} />
    </Stack>
  );
}
""" > "app/_layout.tsx"


echo """import { Tabs } from 'expo-router';

export default function TabLayout() {
  return (
    <Tabs>
      <Tabs.Screen name='index' options={{ title: 'Home' }} />
      <Tabs.Screen name='about' options={{ title: 'About' }} />
    </Tabs>
  );
}
""" > "app/(tabs)/_layout.tsx"
```

# Chapter 3: Build a screen

Installed required dependencies

```bash
npx expo install expo-image
```

Create folder to organize components

```bash
mkdir components # Assuming you are in StickerSmash folder and not in repo's root folder. Otherwise, do `cd StickerSmash` first
```

Add new component ImageViewer:

```bash
echo """import { ImageSourcePropType, StyleSheet } from 'react-native';
import { Image } from 'expo-image';

type Props = {
  imgSource: ImageSourcePropType;
};

export default function ImageViewer({ imgSource }: Props) {
  return <Image source={imgSource} style={styles.image} />;
}

const styles = StyleSheet.create({
  image: {
    width: 320,
    height: 440,
    borderRadius: 18,
  },
});""" > components/ImageViewer.tsx
```

Add new component Button:

```bash
echo """import { StyleSheet, View, Pressable, Text } from 'react-native';

type Props = {
  label: string;
};

export default function Button({ label }: Props) {
  return (
    <View style={styles.buttonContainer}>
      <Pressable style={styles.button} onPress={() => alert('You pressed a button.')}>
        <Text style={styles.buttonLabel}>{label}</Text>
      </Pressable>
    </View>
  );
}

const styles = StyleSheet.create({
  buttonContainer: {
    width: 320,
    height: 68,
    marginHorizontal: 20,
    alignItems: 'center',
    justifyContent: 'center',
    padding: 3,
  },
  button: {
    borderRadius: 10,
    width: '100%',
    height: '100%',
    alignItems: 'center',
    justifyContent: 'center',
    flexDirection: 'row',
  },
  buttonLabel: {
    color: '#fff',
    fontSize: 16,
  },
});""" > components/Button.tsx
```
# Chapter 4: Use an image picker