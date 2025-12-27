import 'package:flutter/material.dart';

void main() {
  runApp(const TapGame());
}

class TapGame extends StatelessWidget {
  const TapGame({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: GamePage(),
    );
  }
}

class GamePage extends StatefulWidget {
  const GamePage({super.key});

  @override
  State<GamePage> createState() => _GamePageState();
}

class _GamePageState extends State<GamePage> {
  int score = 0;

  void increaseScore() {
    setState(() {
      score++;
    });
  }

  void resetGame() {
    setState(() {
      score = 0;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
      appBar: AppBar(
        title: const Text('لعبة النقر'),
        backgroundColor: Colors.deepPurple,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text(
              'النقاط',
              style: TextStyle(color: Colors.white, fontSize: 28),
            ),
            const SizedBox(height: 10),
            Text(
              score.toString(),
              style: const TextStyle(
                color: Colors.yellow,
                fontSize: 60,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 30),
            ElevatedButton(
              onPressed: increaseScore,
              style: ElevatedButton.styleFrom(
                padding: const EdgeInsets.all(20),
              ),
              child: const Text(
                'اضغط',
                style: TextStyle(fontSize: 24),
              ),
            ),
            const SizedBox(height: 15),
            TextButton(
              onPressed: resetGame,
              child: const Text(
                'إعادة',
                style: TextStyle(color: Colors.red, fontSize: 18),
              ),
            )
          ],
        ),
      ),
    );
  }
}
