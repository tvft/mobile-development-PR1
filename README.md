# Практическая работа №1 Знакомство с Android Studio
Выполнила: Тристан Владислава Дмитриевна ИНС-б-о-24-2 Вариант:9
Цель работы 
Изучение интерфейса Android studio и создание первого простого приложения 
Ход работы
1. В начале работы был скачан и настроен Android Studio согласно методичке. Был создан и запущен новый проект "My Application"
<img width="2096" height="1389" alt="Снимок экрана 2026-03-02 183653" src="https://github.com/user-attachments/assets/2fac3b4b-bb42-474b-8d68-0cd46be72dd7" />
2. В названии приложения указано авторство путем изменения содержимого файла "strings.xml"<img width="621" height="160" alt="Снимок экрана 2026-03-02 185330" src="https://github.com/user-attachments/assets/725f9a3a-edcb-41ba-b876-cd5623ec26b3" />

На странице приложения указана дата рождения с помощью свойства страницы TextView.
<img width="2121" height="1354" alt="2026-03-02_18-56-09" src="https://github.com/user-attachments/assets/39a3f347-4b81-449b-9b74-fdf0e57fd0fe" />

3. На третьем  этапе было выполнено индивидуальное задание согласно варианту. В соответствии с условием, был отрисован оранжевый квадрат, площадь которого в 2 раза меньшн площади экрана.

# Листинг 1 - Класс Drawview для задания 3
package com.example.myapplication;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // Создаем и показываем наш DrawView
        DrawView drawView = new DrawView(this);
        setContentView(drawView);

        setTitle("Оранжевый квадрат");
    }
}

class DrawView extends View {

    private Paint paint;

    public DrawView(Context context) {
        super(context);
        paint = new Paint();
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);

        // Получаем ширину и высоту экрана
        int screenWidth = getWidth();
        int screenHeight = getHeight();

        // Площадь экрана = screenWidth * screenHeight
        // Площадь квадрата = сторона^2
        // По условию: сторона^2 = (screenWidth * screenHeight) / 2
        // Значит: сторона = sqrt((screenWidth * screenHeight) / 2)

        double screenArea = screenWidth * screenHeight;
        double squareArea = screenArea / 2; // площадь квадрата в 2 раза меньше
        int sideLength = (int) Math.sqrt(squareArea); // сторона квадрата

        // Заливаем фон белым
        canvas.drawRGB(255, 255, 255);

        // Рисуем оранжевый квадрат
        paint.setColor(Color.parseColor("#FFA500")); // Оранжевый цвет
        paint.setStyle(Paint.Style.FILL);

        // Центрируем квадрат на экране
        int left = (screenWidth - sideLength) / 2;
        int top = (screenHeight - sideLength) / 2;
        int right = left + sideLength;
        int bottom = top + sideLength;

        canvas.drawRect(left, top, right, bottom, paint);


    }
}
