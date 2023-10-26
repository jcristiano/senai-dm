---
id: exemplo-sala-codigo-stateless
slug: exemplo-sala-codigo-stateless
title: Exemplo Stateless Widget
sidebar_position: 1
tags:
    - flutter
    - widget
    - stateless
---

# Exemplo de código abordado em sala de aula
```dart title="statelessView.dart"
import 'package:flutter/material.dart';

void main(List<String> args){
  runApp(QuestionarioApp());
}

class QuestionarioApp extends StatelessWidget{
  
  final List<String> minhasPerguntas = [
    "Primeira Pergunta",
    "Segunda Pergunta",
    "Terceira Pergunta"
  ];

  int indiceDaPergunta = 0;

  void trocarPerguntar(int index){
    indiceDaPergunta = index;
    print("Voce selecionou a pergunta: \"${minhasPerguntas.elementAt(index)}\"");
  }

  @override
  Widget build(BuildContext context) {
    return(MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text("Questionario")),
        body: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Container(),
            Text(minhasPerguntas.elementAt(indiceDaPergunta)),
            ElevatedButton(onPressed: () => trocarPerguntar(0), child: const Text("Primeira Pergunta"),),
            ElevatedButton(onPressed: () => trocarPerguntar(1), child: const Text("Segunda Pergunta"),),
            ElevatedButton(onPressed: () => trocarPerguntar(2), child: const Text("Terceira Pergunta"),),
          ],
        ),
      ),
    ));
  }

}
```

## Como incluir uma espaçamento entre os botões

Para essa ação é possível incluir um padding para "envelopar" os nossos botões. 

```dart
Padding
```

Assim ficaria nosso código ajustado:

```dart
import 'package:flutter/material.dart';

void main(List<String> args){
  runApp(QuestionarioApp());
}

class QuestionarioApp extends StatelessWidget{
  
  final List<String> minhasPerguntas = [
    "Primeira Pergunta",
    "Segunda Pergunta",
    "Terceira Pergunta"
  ];

  int indiceDaPergunta = 0;

  void trocarPerguntar(int index){
    indiceDaPergunta = index;
    print("Voce selecionou a pergunta: \"${minhasPerguntas.elementAt(index)}\"");
  }

  @override
  Widget build(BuildContext context) {
    return(MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text("Questionario")),
        body: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Container(),
            Text(minhasPerguntas.elementAt(indiceDaPergunta)),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: ElevatedButton(onPressed: () => trocarPerguntar(0), child: const Text("Primeira Pergunta"),),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: ElevatedButton(onPressed: () => trocarPerguntar(1), child: const Text("Segunda Pergunta"),),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: ElevatedButton(onPressed: () => trocarPerguntar(2), child: const Text("Terceira Pergunta"),),
            ),
          ],
        ),
      ),
    ));
  }

}
```
