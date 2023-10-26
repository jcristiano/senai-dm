---
id: troca-para-gestao-de-estado
slug: troca-para-gestao-de-estado
title: Mudança para gestão de estados
sidebar_position: 2
tags:
    - flutter
    - widget
    - stateless
---

# Como converter um componente sem estado para um com estado gerenciado

## Devemos tomar como exemplo a classe de Questionario sem estado

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

## Criacao de um estado

O primeiro aspecto para criar um componente com gestão de estado é trocar a nossa classe que **herda** de StatelessWidget para o tipo State.

No segundo, criar um classe que herde de StatefullWidget e implemente o método de gestão de estado.

Segue a alteração proposta:

```dart title="statefull.dart"
import 'package:flutter/material.dart';

void main(List<String> args){
  runApp(QuestionarioApp());
}

class QuestionarioApp extends StatefulWidget{
  
  @override
  State<StatefulWidget> createState() {
    return QuestionarioState();
  }

}

class QuestionarioState extends State<QuestionarioApp>{
  
  final List<String> minhasPerguntas = [
    "Primeira Pergunta",
    "Segunda Pergunta",
    "Terceira Pergunta"
  ];

  int indiceDaPergunta = 0;

  void trocarPerguntar(int index){
    setState((){
      indiceDaPergunta = index;
    });
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

:::info
Essa mudança ainda não é suficiente para conquistar o comportamento esperado.
Para isso ocorrer, é necessário notificar a mudança do nosso estado.
:::

## Agora é com vocês

Desenvolva um programa com um componente Text e com 2 botões, um para incrementar um contador e outro para decrementar um contador.

A cada mudança do contador o valor deve ser exibido no componente Text.

