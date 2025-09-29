#include #include #include using namespace std;

// Класс с закрытыми свойствами и открытыми методами class MyClass { private: int id; // Идентификатор string name; // Строковое поле 1 string type; // Строковое поле 2 string category; // Строковое поле 3 int intField; // Целое число float floatField; // Число с плавающей точкой double doubleField; // Число с двойной точностью

public: // Конструктор по умолчанию MyClass() : id(0), name(""), type(""), category(""), intField(0), floatField(0.0), doubleField(0.0) {}

// Конструктор с параметрами
MyClass(int i, string n, string t, string c, int iF, float fF, double dF) 
    : id(i), name(n), type(t), category(c), intField(iF), floatField(fF), doubleField(dF) {}

// Метод для редактирования свойств
void setProperties(int i, string n, string t, string c, int iF, float fF, double dF) {
    id = i;
    name = n;
    type = t;
    category = c;
    intField = iF;
    floatField = fF;
    doubleField = dF;
}

// Метод для отображения свойств объекта
void displayProperties() const {
    cout << "ID: " << id << ", Name: " << name << ", Type: " << type 
         << ", Category: " << category << ", IntField: " << intField 
         << ", FloatField: " << floatField << ", DoubleField: " << doubleField << endl;
}

// Геттер для ID
int getId() const { return id; }

// Функция для создания объекта по умолчанию void createDefaultObject(vector& objects) { objects.push_back(MyClass()); cout << "Объект по умолчанию создан.\n"; }

// Функция для создания объекта с параметрами void createObjectWithParameters(vector& objects) { int id, intField; string name, type, category; float floatField; double doubleField;

cout << "Введите значения (id, name, type, category, intField, floatField, doubleField): ";
cin >> id >> name >> type >> category >> intField >> floatField >> doubleField;

objects.emplace_back(id, name, type, category, intField, floatField, doubleField);
cout << "Объект с параметрами создан.\n";
}

// Функция для создания массива объектов void createArrayOfObjects(vector& objects) { int count; cout << "Сколько объектов создать? "; cin >> count;

for (int i = 0; i < count; ++i) {
    cout << "Создание объекта " << i + 1 << ":\n";
    createObjectWithParameters(objects);
}
}

// Функция для редактирования объекта void editObject(vector& objects) { int id; cout << "Введите ID объекта для редактирования: "; cin >> id;

for (auto& obj : objects) {
    if (obj.getId() == id) {
        int newId, intField;
        string name, type, category;
        float floatField;
        double doubleField;

        cout << "Введите новые значения (id, name, type, category, intField, floatField, doubleField): ";
        cin >> newId >> name >> type >> category >> intField >> floatField >> doubleField;

        obj.setProperties(newId, name, type, category, intField, floatField, doubleField);
        cout << "Объект обновлён.\n";
        return;
    }
}
cout << "Объект с таким ID не найден.\n";
}

// Функция для просмотра всех объектов void displayAllObjects(const vector& objects) { if (objects.empty()) { cout << "Список объектов пуст.\n"; return; }

cout << "Список объектов:\n";
for (const auto& obj : objects) {
    obj.displayProperties();
}
}

// Главное меню программы int main() { vector objects; int choice;

while (true) {
    cout << "\nМеню:\n";
    cout << "1. Создать объект по умолчанию\n";
    cout << "2. Создать объект с параметрами\n";
    cout << "3. Создать массив объектов\n";
    cout << "4. Редактировать объект\n";
    cout << "5. Просмотреть все объекты\n";
    cout << "6. Выход\n";
    cout << "Выберите действие: ";
    cin >> choice;

    switch (choice) {
        case 1:
            createDefaultObject(objects);
            break;
        case 2:
            createObjectWithParameters(objects);
            break;
        case 3:
            createArrayOfObjects(objects);
            break;
        case 4:
            editObject(objects);
            break;
        case 5:
            displayAllObjects(objects);
            break;
        case 6:
            cout << "Выход из программы.\n";
            return 0;
        default:
            cout << "Неверный выбор. Попробуйте снова.\n";
    }
}
}# lab4
