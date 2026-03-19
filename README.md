### Просто переписал ваш же код (LoginPage) под домашнее задание

```
import 'package:flutter/material.dart';

class Login extends StatefulWidget {
  const Login({super.key});

  @override
  LoginState createState() => LoginState();
}

class LoginState extends State<Login> {
  double width = 50;
  double height = 50;
  Color boxColor = Colors.amber;
  bool viewBox = false;

  TextEditingController widthController = TextEditingController();
  TextEditingController heightController = TextEditingController();
  TextEditingController colorController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Box Builder"),
      ),
      body: Form(
        child: Column(
          children: [
            Container(
              margin: const EdgeInsets.all(8),
              child: TextFormField(
                controller: widthController,
                keyboardType: TextInputType.number,
                decoration: const InputDecoration(
                  label: Text("Width"),
                ),
              ),
            ),

            Container(
              margin: const EdgeInsets.all(8),
              child: TextFormField(
                controller: heightController,
                keyboardType: TextInputType.number,
                decoration: const InputDecoration(
                  label: Text("Height"),
                ),
              ),
            ),

            Container(
              margin: const EdgeInsets.all(8),
              child: TextFormField(
                controller: colorController,
                decoration: const InputDecoration(
                  label: Text("Color (red, blue, green...)"),
                ),
              ),
            ),

            ElevatedButton(
              onPressed: () {
                setState(() {
                  width = double.tryParse(widthController.text) ?? 50;
                  height = double.tryParse(heightController.text) ?? 50;
                  boxColor = getColor(colorController.text);
                  viewBox = true;
                });
              },
              child: const Text("Create Box"),
            ),

            const SizedBox(height: 20),

            Text("Width: $width, Height: $height"),

            const SizedBox(height: 20),

            viewBox
                ? Container(
                    width: width,
                    height: height,
                    decoration: BoxDecoration(
                      color: boxColor,
                      border: Border.all(color: Colors.black),
                    ),
                  )
                : const SizedBox(),
          ],
        ),
      ),
    );
  }

  Color getColor(String colorName) {
    switch (colorName.toLowerCase()) {
      case "red":
        return Colors.red;
      case "blue":
        return Colors.blue;
      case "green":
        return Colors.green;
      case "yellow":
        return Colors.yellow;
      case "black":
        return Colors.black;
      default:
        return Colors.amber; 
    }
  }
}
```
