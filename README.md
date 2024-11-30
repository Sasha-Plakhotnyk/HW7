#Homework 7
#Користування калькулятором: 1. Введіть дію 2. Введіть перше число дію друге число
#Приклад: +; 7 + 8; 15
class Calculator:
    def init(self):
        self.add = '+'
        self.sub = '-'
        self.mul = '*'
        self.div = '/'

    def _validate_and_convert(self, a, b):
        try:
            a = float(a)
            b = float(b)
            return a, b
        except ValueError:
            raise ValueError("Обидва мають бути числами")

    def _safe_divide(self, a, b):
        if b == 0:
            raise ZeroDivisionError("Ділення на нуль неможливе! Змініть значеня b")
        return a / b

    def _operate(self, a, b, operation):
        a, b = self._validate_and_convert(a, b)
        
        if operation == self.add: #додавання
            return a + b
        elif operation == self.sub: #віднімання
            return a - b
        elif operation == self.mul: #множення
            return a * b
        elif operation == self.div: #ділення
            return self._safe_divide(a, b)
        else:
            raise ValueError("Невідома операція!")

    def add(self, a, b):
        return self._operate(a, b, self.add)

    def subtract(self, a, b):
        return self._operate(a, b, self.sub)

    def multiply(self, a, b):
        return self._operate(a, b, self.mul)

    def divide(self, a, b):
        return self._operate(a, b, self.div)
