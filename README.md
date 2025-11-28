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