# module_3_hard
Дополнительное практическое задание по модулю: "Подробнее о функциях."
def calculate_structure_sum(info):
    # Инициализация переменной для хранения суммы
    a = 0
    
    # Если info - целое число или число с плавающей запятой, возвращаем его как есть
    if isinstance(info, int) or isinstance(info, float):
        return info
    
    # Если info - строка, возвращаем длину строки
    elif isinstance(info, str):
        return len(info)
    
    # Если info - список, проходим по каждому элементу и рекурсивно суммируем значения
    elif isinstance(info, list):
        for item in info:
            a += calculate_structure_sum(item)  # Добавляем результат вызова для каждого элемента
        return a
    
    # Если info - кортеж, выполняем аналогичные действия, как для списка
    elif isinstance(info, tuple):
        for item in info:
            a += calculate_structure_sum(item)
        return a
    
    # Если info - множество, также проходим по каждому элементу
    elif isinstance(info, set):
        for item in info:
            a += calculate_structure_sum(item)
        return a
    
    # Если info - словарь, суммируем ключи (значения не учитываются)
    elif isinstance(info, dict):
        for key in info.items():
            a += calculate_structure_sum(key)  # Суммируем только ключи словаря
        return a
    
    # Если тип не поддерживается, возвращаем 0
    else:
        return 0

# Пример структуры данных, которую мы хотим обработать
data_structure = [
  [1, 2, 3],                            # Список чисел
  {'a': 4, 'b': 5},                     # Словарь с двумя ключами
  (6, {'cube': 7, 'drum': 8}),          # Кортеж, содержащий число и словарь
  "Hello",                               # Строка
  ((), [{(2, 'Urban', ('Urban2', 35))}])  # Кортеж с вложенной структурой
]

# Вызываем функцию для расчета суммы по структуре данных и сохраняем результат
result = calculate_structure_sum(data_structure)
# Печатаем итоговый результат
print(result)
