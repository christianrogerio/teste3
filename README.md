# teste3
This example shows how to use a static variable into a class.
I think it is better than use Context API in some cases.


Class static:

export default class Lapis {
     static cont = 'oi';
     static c=0;
}


To use em other file:
import React from 'react'
import {Text} from 'react-native'
import Lapis from './Lapis'

export default props => {
    return (
        <>
        <Text>{Lapis.c}</Text>
        </>
        );
}


How to change the value of the variable static into the class:

/**
 * Sample React Native App
 * https://github.com/facebook/react-native
 *
 * @format
 * @flow strict-local
 */

import React, {useState} from 'react';
import { Button } from 'react-native';
import type {Node} from 'react';
import {
  SafeAreaView,
  ScrollView,
  StatusBar,
  StyleSheet,
  Text,
  useColorScheme,
  View,
} from 'react-native';

import {
  Colors,
  DebugInstructions,
  Header,
  LearnMoreLinks,
  ReloadInstructions,
} from 'react-native/Libraries/NewAppScreen';

import Lapis from './src/Lapis'
import Texto from './src/Texto'

var EST = 'TESTE';


const Section = ({children, title}): Node => {
  const isDarkMode = useColorScheme() === 'dark';

  
  return (
    <View style={styles.sectionContainer}>
      <Text
        style={[
          styles.sectionTitle,
          {
            color: isDarkMode ? Colors.white : Colors.black,
          },
        ]}>
        {title}
      </Text>
      <Text
        style={[
          styles.sectionDescription,
          {
            color: isDarkMode ? Colors.light : Colors.dark,
          },
        ]}>
        {children}
      </Text>
    </View>
  );
};

const App: () => Node = () => {
  const [exibirCont, setCont] = useState(Lapis.cont)
  const isDarkMode = useColorScheme() === 'dark';

  const backgroundStyle = {
    backgroundColor: isDarkMode ? Colors.darker : Colors.lighter,
  };

  function mudarCont(valor){
    Lapis.cont = valor;
    Lapis.c++;
    setCont(Lapis.c.toString())
  }

  EST='MUDOU';
  Lapis.cont='mudou2';
  return (
    <SafeAreaView style={backgroundStyle}>
      <StatusBar barStyle={isDarkMode ? 'light-content' : 'dark-content'} />
      <ScrollView
        contentInsetAdjustmentBehavior="automatic"
        style={backgroundStyle}>          
        <Header />
        <View
          style={{
            backgroundColor: isDarkMode ? Colors.black : Colors.white,
          }}>
            <Button title='Mudar' onPress={()=>{mudarCont('clicou novo')}}></Button> 
          <Section title={exibirCont}>
          <Text>Abaixo texto: [</Text>
            <Texto/>
            <Text>]</Text>
            Edit <Text style={styles.highlight}>App.js</Text> to change this
            screen and then come back to see your edits.
          </Section>
          <Section title="See Your Changes">
            <ReloadInstructions />
          </Section>
          <Section title="Debug">
            <DebugInstructions />
          </Section>
          <Section title="Learn More">
            Read the docs to discover what to do next:
          </Section>
          <LearnMoreLinks />
        </View>
      </ScrollView>
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  sectionContainer: {
    marginTop: 32,
    paddingHorizontal: 24,
  },
  sectionTitle: {
    fontSize: 24,
    fontWeight: '600',
  },
  sectionDescription: {
    marginTop: 8,
    fontSize: 18,
    fontWeight: '400',
  },
  highlight: {
    fontWeight: '700',
  },
});

export default App;

