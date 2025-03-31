import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Enhanced Counter App',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  // دالة لزيادة العداد
  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  // دالة لتقليل العداد
  void _decrementCounter() {
    setState(() {
      _counter--;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Enhanced Counter App'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(
              'Current Count:',
              style: Theme.of(context).textTheme.headline6,
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline2,
            ),
          ],
        ),
      ),
      floatingActionButton: Row(
        mainAxisAlignment: MainAxisAlignment.end,
        children: [
          // زر التصغير
          FloatingActionButton(
            heroTag: 'decrement', // مهم لتجنب أخطاء Hero animation
            onPressed: _decrementCounter,
            tooltip: 'Decrement',
            child: Icon(Icons.remove),
            backgroundColor: Colors.red, // لون مميز للزر
          ),
          SizedBox(width: 10), // مسافة بين الزرين
          // زر التكبير
          FloatingActionButton(
            heroTag: 'increment',
            onPressed: _incrementCounter,
            tooltip: 'Increment',
            child: Icon(Icons.add),
          ),
        ],
      ),
    );
  }
}
