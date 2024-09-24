# Laporan Praktikum LP_02

## Apa itu Dart?
Dart adalah bahasa pemrograman yang dikembangkan oleh Google. Dart dirancang untuk membangun aplikasi yang dapat berjalan di berbagai platform, termasuk web, mobile, dan desktop. Dart adalah bahasa yang berorientasi objek dan mendukung pengembangan aplikasi yang efisien dengan sintaksis yang mudah dipahami.

## Apa itu Flutter?
Flutter adalah framework open-source yang juga dikembangkan oleh Google untuk membangun aplikasi mobile, web, dan desktop dari satu basis kode. Flutter menggunakan bahasa pemrograman Dart dan menyediakan berbagai widget yang memungkinkan pengembang untuk membuat antarmuka pengguna yang kaya dan responsif.

## Contoh Widget pada Flutter
Berikut adalah contoh kode Flutter yang menampilkan biodata pengguna dengan berbagai widget:


## Hasil Codingan

![App Screenshot](/image.png)


## Code Program
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(
            seedColor: const Color.fromARGB(255, 46, 162, 17)),
        useMaterial3: true,
      ),
      home: const MyHomePage(title: 'My Profile'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({super.key, required this.title});

  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: Text(widget.title),
      ),
      body: Center(
        // Wrap Column with Center to center all the content
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          crossAxisAlignment:
              CrossAxisAlignment.center, // Ensures horizontal centering
          children: <Widget>[
            // Widget 1: CircleAvatar for profile picture wrapped in a Container
            Container(
              padding: const EdgeInsets.all(8), // Adding some padding
              decoration: BoxDecoration(
                shape: BoxShape.circle,
                border: Border.all(
                    color: Colors.greenAccent, width: 3), // Adding border
              ),
              child: const CircleAvatar(
                radius: 50,
                backgroundImage: NetworkImage(
                    '/lib/image.jpg'), // Ganti dengan URL foto profil Anda
              ),
            ),
            const SizedBox(height: 16),

            // Container for personal information
            Container(
              padding: const EdgeInsets.all(16),
              margin: const EdgeInsets.symmetric(horizontal: 20),
              decoration: BoxDecoration(
                color: Colors.grey[200],
                borderRadius: BorderRadius.circular(10),
              ),
              child: Column(
                crossAxisAlignment:
                    CrossAxisAlignment.center, // Center the text
                children: const <Widget>[
                  // Widget 2: Nama
                  Text(
                    'Qadri Aditya Hadi Ramadhan',
                    style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
                  ),

                  // Widget 3: Umur
                  Text('Umur: 22'),

                  // Widget 4: Pekerjaan
                  Text('Mahasiswa'),

                  // Widget 5: Hobi
                  Text('Hobi: Sports'),

                  // Widget 6: Kalimat motivasi
                  Text('Keep Learning'),
                ],
              ),
            ),

            const SizedBox(height: 16),

            // Container for counter section
            Container(
              padding: const EdgeInsets.all(16),
              margin: const EdgeInsets.symmetric(horizontal: 20),
              decoration: BoxDecoration(
                color: Colors.blue[100],
                borderRadius: BorderRadius.circular(10),
              ),
              child: Column(
                children: <Widget>[
                  // Widget 6: Text showing counter message
                  const Text(
                    'You have pushed the button this many times:',
                  ),

                  // Widget 7: Counter display
                  Text(
                    '$_counter',
                    style: Theme.of(context).textTheme.headlineMedium,
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
      // FloatingActionButton to increment the counter
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
    );
  }
}
