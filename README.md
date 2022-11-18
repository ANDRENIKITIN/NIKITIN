from PyQt5.QtWidgets import QWidget, QApplication, QLabel, QPushButton, QFontComboBox
import sys
from PyQt5.QtCore import Qt, QDir
from PyQt5.QtGui import QFont, QFontDatabase
from PyQt5.QtWidgets import QApplication, QLabel


class Calculator(QWidget):
    def __init__(self):
        super().__init__()
        self.initUI()
        self.my_input = []  # для ввода цифр
        self.operand_1 = []  # для первого операнда
        self.operand_2 = []  # для второго операнда

    def initUI(self):
        self.setGeometry(150, 200, 250, 300)  # 3й - Ширина окна, 4й - Высота окна
        self.setWindowTitle("КУЛькулятор")

        self.label = QLabel(self)
        self.label.setText('0')
        self.label.setFont(QFont('Algerian', 10))  # размер шрифта текста
        self.label.resize(250, 55)  # Размер строки (должен коррелировать с шириной окна)
        self.label.move(5, 0)  # Положение текста
        self.move(50, 50)  # Положение Окна

        # if

        self.num_1 = QPushButton('1', self)
        self.num_1.resize(40, 40)  # размер кнопки
        self.num_1.move(5, 50)  # положение кнопки горизонт, вертикаль
        self.num_1.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_2 = QPushButton('2', self)
        self.num_2.resize(40, 40)
        self.num_2.move(50, 50)  # координаты кнопки: горизонт, вертикаль
        self.num_2.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_3 = QPushButton('3', self)
        self.num_3.resize(40, 40)
        self.num_3.move(95, 50)  # координаты кнопки: горизонт, вертикаль
        self.num_3.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.div = QPushButton('/', self)
        self.div.resize(40, 40)
        self.div.move(140, 50)
        self.num_3.setFont(QFont('Algerian', 14))  # шрифт кнопки

        self.num_4 = QPushButton('4', self)
        self.num_4.resize(40, 40)
        self.num_4.move(5, 95)
        self.num_4.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_5 = QPushButton('5', self)
        self.num_5.resize(40, 40)
        self.num_5.move(50, 95)
        self.num_5.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_6 = QPushButton('6', self)
        self.num_6.resize(40, 40)
        self.num_6.move(95, 95)
        self.num_6.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.mul = QPushButton('*', self)
        self.mul.resize(40, 40)
        self.mul.move(140, 95)
        self.mul.setFont(QFont('Algerian', 14))  # шрифт кнопки

        self.num_7 = QPushButton('7', self)
        self.num_7.resize(40, 40)
        self.num_7.move(5, 140)
        self.num_7.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_8 = QPushButton('8', self)
        self.num_8.resize(40, 40)
        self.num_8.move(50, 140)
        self.num_8.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_9 = QPushButton('9', self)
        self.num_9.resize(40, 40)
        self.num_9.move(95, 140)
        self.num_9.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.plus = QPushButton('+', self)
        self.plus.resize(40, 40)
        self.plus.move(140, 140)
        self.plus.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_0 = QPushButton('0', self)
        self.num_0.resize(40, 40)
        self.num_0.move(5, 185)
        self.num_0.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.minus = QPushButton('-', self)
        self.minus.resize(40, 40)
        self.minus.move(140, 185)
        self.minus.setFont(QFont('Algerian', 14))  # шрифт кнопки

        self.equal = QPushButton('=', self)
        self.equal.resize(40, 40)
        self.equal.move(95, 185)
        self.equal.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.root = QPushButton('√', self)
        self.root.resize(40, 40)
        self.root.move(50, 185)
        self.root.setFont(QFont('Algerian', 12))  # шрифт кнопки

        #  HW >>>>>>>>>> Дополните код предыдущего модуля. Добавьте кнопки %, // и возведение в квадрат.
        self.perc = QPushButton('%', self)
        self.perc.resize(40, 40)
        self.perc.move(5, 230)
        self.perc.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.h_div = QPushButton('//', self)
        self.h_div.resize(40, 40)
        self.h_div.move(50, 230)
        self.h_div.setFont(QFont('Algerian', 11))  # шрифт кнопки

        self.sqrt = QPushButton('**', self)
        self.sqrt.resize(40, 40)
        self.sqrt.move(95, 230)
        self.sqrt.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.delt = QPushButton('C', self)
        self.delt.resize(40, 40)
        self.delt.move(140, 230)
        self.delt.setFont(QFont('Algerian', 12))  # шрифт кнопки

        self.num_1.clicked.connect(self.one)  # привязка кнопок к их функциям
        self.num_2.clicked.connect(self.two)  # ...
        self.num_3.clicked.connect(self.three)  # ...
        self.num_4.clicked.connect(self.four)  # ...
        self.num_5.clicked.connect(self.five)  # ...
        self.num_6.clicked.connect(self.six)  # ...
        self.num_7.clicked.connect(self.seven)  # ...
        self.num_8.clicked.connect(self.eight)  # ...
        self.num_9.clicked.connect(self.nine)  # ...
        self.num_0.clicked.connect(self.zero)  # ...
        self.plus.clicked.connect(self.plus_1)
        self.minus.clicked.connect(self.minus_1)
        self.mul.clicked.connect(self.mul_1)
        self.div.clicked.connect(self.div_1)
        # self.step.clicked.connect(self.step_1)
        self.root.clicked.connect(self.root_1)
        self.equal.clicked.connect(self.equal_1)
        self.delt.clicked.connect(self.clean)
        # HW >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
        self.perc.clicked.connect(self.perc_1)
        self.h_div.clicked.connect(self.h_div_1)
        self.sqrt.clicked.connect(self.sqrt_1)

    def enterValue(self):  # проверяет
        if self.label.text() == '0':  # если на каль-ре ничего нет
            self.label.setText('')  # стирает всё,
        self.label.setText(self.label.text() + self.my_input)  # иначе - добавляет к имеющемуся вводу новый ввод данных

    def one(self):  # функция для нажатия кнопки "1"
        self.my_input = '1'   # новый ввод данных
        self.enterValue()  # ВЫЗОВ ДРУГОЙ ФУНКЦИИ

    def two(self):  # функция кнопки "2"
        self.my_input = '2'
        self.enterValue()

    def three(self):
        self.my_input = '3'
        self.enterValue()

    def four(self):
        self.my_input = '4'
        self.enterValue()

    def five(self):
        self.my_input = '5'
        self.enterValue()

    def six(self):
        self.my_input = '6'
        self.enterValue()

    def seven(self):
        self.my_input = '7'
        self.enterValue()

    def eight(self):
        self.my_input = '8'
        self.enterValue()

    def nine(self):
        self.my_input = '9'
        self.enterValue()

    def zero(self):
        self.my_input = '0'
        self.enterValue()

    def plus_1(self):  #
        self.operation = '+'  # при нажатии плюса
        self.operand_1 = float(self.label.text())
        # self.label.text())  # присваиваем всё что есть в тексте переменной _1  и меняем на float чтобы считать
        # self.label.setText('')  # очищает  строку после нажатия на кнопку операции
        self.label.setText('')

    def minus_1(self):
        self.operation = '-'
        self.operand_1 = float(self.label.text())
        self.label.setText('')

    def mul_1(self):
        self.operation = '*'
        self.operand_1 = float(self.label.text())
        self.label.setText('')

    def div_1(self):
        self.operation = '/'
        self.operand_1 = float(self.label.text())
        self.label.setText('')

    def root_1(self):
        self.operation = '√'
        self.operand_1 = float(self.label.text())
        self.label.setText('')

    # HW %%%%%%%%%%%%%%%%%%%%%%%%%%>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
    def perc_1(self):  # функция %
        self.operatin = '%'
        self.operand_2 = float(self.label.text())       # ЗАбирает цифры после очищения кнопкой функции - второй операнд
        self.operand_2 = (self.operand_1 * self.operand_2) / float('100')
        print(self.operand_1)
        print(self.operand_2)
        if self.operation == '+':
            self.rezult = self.operand_1 + self.operand_2
        elif self.operation == '-':
            self.rezult = self.operand_1 - self.operand_2
        elif self.operation == '*':
            self.rezult = self.operand_1 * self.operand_2
        elif self.operation == '/':
            if self.operand_2 == 0:
                self.rezult = 'error'
            else:
                self.rezult = self.operand_1 / self.operand_2
        elif self.operation == '^':
            self.rezult = self.operand_1 ** self.operand_2

        elif self.operation == '√':
            self.rezult = self.operand_1 ** (1 / self.operand_2)

        self.label.setText(str(self.rezult))

    def h_div_1(self):
        self.operation = '//'
        self.operand_1 = float(self.label.text())
        self.label.setText('')

    def sqrt_1(self):           # HW >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>.
        self.operation = '**'
        self.operand_1 = float(self.label.text())
        self.rezult = self.operand_1 * self.operand_1
        self.label.setText(str(self.rezult))

    def equal_1(self):
        self.operand_2 = float(self.label.text())
        if self.operation == '+':
            self.rezult = self.operand_1 + self.operand_2
        elif self.operation == '-':
            self.rezult = self.operand_1 - self.operand_2
        elif self.operation == '*':
            self.rezult = self.operand_1 * self.operand_2
        elif self.operation == '/':
            if self.operand_2 == 0:
                self.rezult = 'error'
            else:
                self.rezult = self.operand_1 / self.operand_2

        elif self.operation == '//':
            if self.operand_2 == 0:
                self.rezult = 'error'
            else:
                self.rezult = self.operand_1 // self.operand_2

        elif self.operation == '^':
            self.rezult = self.operand_1 ** self.operand_2

        elif self.operation == '√':
            self.rezult = self.operand_1 ** (1 / self.operand_2)

        self.label.setText(str(self.rezult))

    def clean(self):
        self.label.setText('')


if __name__ == '__main__':
    app = QApplication(sys.argv)
    ex = Calculator()
    ex.show()
    sys.exit(app.exec())
