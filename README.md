# Repositorio-Programacion - 2
Repositorio para fundamentos de programacion

Practico 9


1 Función POTEN(x, y): potencia de dos números reales
#include <iostream>
#include <cmath>
using namespace std;

double POTEN(double x, double y) {
    return pow(x, y);
}

int main() {
    double base, exponente;
    cout << "Ingrese la base: ";
    cin >> base;
    cout << "Ingrese el exponente: ";
    cin >> exponente;

    cout << "Resultado: " << POTEN(base, exponente) << endl;
    return 0;
}

2 Función FAC(n): factorial de un entero
#include <iostream>
using namespace std;

long long FAC(int n) {
    long long f = 1;
    for (int i = 1; i <= n; i++) f *= i;
    return f;
}

int main() {
    int n;
    cout << "Ingrese un número entero: ";
    cin >> n;
    cout << "Factorial de " << n << " es: " << FAC(n) << endl;
    return 0;
}


3 Serie S = x¹/1! + x²/2! + ... + xⁿ/n!
#include <iostream>
#include <cmath>
using namespace std;

long long FAC(int n) {
    long long f = 1;
    for (int i = 1; i <= n; i++) f *= i;
    return f;
}

double POTEN(double x, double y) {
    return pow(x, y);
}

double SERIE(double x, int n) {
    double s = 0;
    for (int i = 1; i <= n; i++)
        s += POTEN(x, i) / FAC(i);
    return s;
}

int main() {
    double x; int n;
    cout << "Ingrese x y n: ";
    cin >> x >> n;
    cout << "Suma de la serie = " << SERIE(x, n) << endl;
    return 0;
}


4 Serie S = x¹/1! - x³/3! + x⁵/5! - ...
#include <iostream>
#include <cmath>
using namespace std;

long long FAC(int n) {
    long long f = 1;
    for (int i = 1; i <= n; i++) f *= i;
    return f;
}

double POTEN(double x, double y) {
    return pow(x, y);
}

double SERIE2(double x, int n) {
    double s = 0;
    int signo = 1;
    for (int i = 1; i <= n; i += 2) {
        s += signo * (POTEN(x, i) / FAC(i));
        signo *= -1;
    }
    return s;
}

int main() {
    double x; int n;
    cout << "Ingrese x y n: ";
    cin >> x >> n;
    cout << "Resultado de la serie: " << SERIE2(x, n) << endl;
    return 0;
}


5 Sistema de ecuaciones 2x2
#include <iostream>
using namespace std;

void SISTEMA(double A, double B, double C, double D, double E, double F, double &X, double &Y) {
    double det = A * E - B * D;
    if (det == 0) {
        cout << "El sistema no tiene solución única." << endl;
        return;
    }
    X = (B * F - C * E) / det;
    Y = (C * D - A * F) / det;
}

int main() {
    double A,B,C,D,E,F,X,Y;
    cout << "Ingrese A B C D E F: ";
    cin >> A >> B >> C >> D >> E >> F;
    SISTEMA(A,B,C,D,E,F,X,Y);
    cout << "Solución: X=" << X << ", Y=" << Y << endl;
    return 0;
}


6 Fecha literal
#include <iostream>
#include <string>
using namespace std;

void LITERAL(int dia, int mes, int anio) {
    string meses[] = {"", "Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio",
                      "Julio", "Agosto", "Septiembre", "Octubre", "Noviembre", "Diciembre"};
    cout << dia << " de " << meses[mes] << " de " << (1900 + anio) << endl;
}

int main() {
    int d,m,a;
    cout << "Ingrese día, mes y año (2 dígitos): ";
    cin >> d >> m >> a;
    LITERAL(d,m,a);
    return 0;
}


7 Combinatorio nCr
#include <iostream>
using namespace std;

long long FAC(int n) {
    long long f = 1;
    for (int i = 1; i <= n; i++) f *= i;
    return f;
}

long long COMBI(int n, int r) {
    return FAC(n) / (FAC(r) * FAC(n - r));
}

int main() {
    int n,r;
    cout << "Ingrese n y r: ";
    cin >> n >> r;
    cout << "Combinatorio (" << n << "," << r << ") = " << COMBI(n, r) << endl;
    return 0;
}


8 Ecuación cuadrática
#include <iostream>
#include <cmath>
using namespace std;

void CUADRATICA(double a, double b, double c) {
    double d = b*b - 4*a*c;
    if (d > 0) {
        double x1 = (-b + sqrt(d)) / (2*a);
        double x2 = (-b - sqrt(d)) / (2*a);
        cout << "Raices reales: x1=" << x1 << ", x2=" << x2 << endl;
    } else if (d == 0) {
        cout << "Raiz doble: x=" << -b / (2*a) << endl;
    } else {
        double real = -b / (2*a);
        double imag = sqrt(-d) / (2*a);
        cout << "Raices complejas: " << real << " ± " << imag << "i" << endl;
    }
}

int main() {
    double a,b,c;
    cout << "Ingrese a, b y c: ";
    cin >> a >> b >> c;
    CUADRATICA(a,b,c);
    return 0;
}


9 Convertir un número binario a decimal
#include <iostream>
#include <cmath>
using namespace std;

int BinarioDecimal(long long bin) {
    int dec = 0, i = 0, dig;
    while (bin != 0) {
        dig = bin % 10;
        dec += dig * pow(2, i);
        i++;
        bin /= 10;
    }
    return dec;
}

int main() {
    long long bin;
    cout << "Ingrese un número binario: ";
    cin >> bin;
    cout << "Equivalente decimal: " << BinarioDecimal(bin) << endl;
    return 0;
}


10 Convertir número a romanos
#include <iostream>
using namespace std;

void ROMANO(int num) {
    int valores[] = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
    string simbolos[] = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

    cout << "Número romano: ";
    for (int i = 0; i < 13; i++) {
        while (num >= valores[i]) {
            cout << simbolos[i];
            num -= valores[i];
        }
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Ingrese un número entre 1 y 3999: ";
    cin >> n;
    ROMANO(n);
    return 0;
}


11 Convertir monto decimal a literal (en bolivianos)
#include <iostream>
#include <string>
using namespace std;

string unidades(int n) {
    string u[] = {"", "uno", "dos", "tres", "cuatro", "cinco", "seis", "siete", "ocho", "nueve"};
    return u[n];
}

string decenas(int n) {
    string d[] = {"", "diez", "veinte", "treinta", "cuarenta", "cincuenta",
                  "sesenta", "setenta", "ochenta", "noventa"};
    if (n < 10) return unidades(n);
    if (n < 20) {
        string e[] = {"diez","once","doce","trece","catorce","quince","dieciséis","diecisiete","dieciocho","diecinueve"};
        return e[n - 10];
    }
    int d1 = n / 10;
    int u1 = n % 10;
    return d[d1] + (u1 ? " y " + unidades(u1) : "");
}

string centenas(int n) {
    string c[] = {"", "ciento", "doscientos", "trescientos", "cuatrocientos",
                  "quinientos", "seiscientos", "setecientos", "ochocientos", "novecientos"};
    if (n == 100) return "cien";
    return c[n / 100] + (n % 100 ? " " + decenas(n % 100) : "");
}

string numeroLiteral(int n) {
    if (n == 0) return "cero";
    if (n < 1000) return centenas(n);
    if (n < 1000000) {
        int miles = n / 1000;
        int resto = n % 1000;
        return (miles == 1 ? "mil" : numeroLiteral(miles) + " mil") + (resto ? " " + centenas(resto) : "");
    }
    return "fuera de rango";
}

int main() {
    double monto;
    cout << "Ingrese monto (ej. 1560.50): Bs ";
    cin >> monto;

    int parteEntera = int(monto);
    int parteDecimal = int((monto - parteEntera) * 100 + 0.5);

    cout << "Literal: " << numeroLiteral(parteEntera) << " " 
         << parteDecimal << "/100 bolivianos" << endl;

    return 0;
}


12 Validar una fecha
#include <iostream>
using namespace std;

bool esBisiesto(int anio) {
    return (anio % 4 == 0 && anio % 100 != 0) || (anio % 400 == 0);
}

bool validarFecha(int d, int m, int a) {
    if (m < 1 || m > 12 || d < 1) return false;
    int diasMes[] = {0,31,28,31,30,31,30,31,31,30,31,30,31};
    if (esBisiesto(a)) diasMes[2] = 29;
    return d <= diasMes[m];
}

int main() {
    int d, m, a;
    cout << "Ingrese día, mes, año: ";
    cin >> d >> m >> a;

    if (validarFecha(d,m,a))
        cout << "Fecha válida ✅" << endl;
    else
        cout << "Fecha inválida ❌" << endl;

    return 0;
}


13 Redondear número real a n decimales
#include <iostream>
#include <cmath>
using namespace std;

double redondear(double num, int decimales) {
    double factor = pow(10, decimales);
    return round(num * factor) / factor;
}

int main() {
    double num; int n;
    cout << "Ingrese número real: ";
    cin >> num;
    cout << "Ingrese cantidad de decimales: ";
    cin >> n;

    cout << "Número redondeado: " << redondear(num, n) << endl;
    return 0;
}


14 Días transcurridos entre dos fechas
#include <iostream>
using namespace std;

bool esBisiesto(int a) {
    return (a % 4 == 0 && a % 100 != 0) || (a % 400 == 0);
}

int diasEnMes(int m, int a) {
    int diasMes[] = {31,28,31,30,31,30,31,31,30,31,30,31};
    if (m == 2 && esBisiesto(a)) return 29;
    return diasMes[m - 1];
}

int convertirADias(int d, int m, int a) {
    int total = 0;
    for (int i = 1; i < a; i++) total += esBisiesto(i) ? 366 : 365;
    for (int i = 1; i < m; i++) total += diasEnMes(i, a);
    total += d;
    return total;
}

int main() {
    int d1,m1,a1,d2,m2,a2;
    cout << "Ingrese primera fecha (d m a): ";
    cin >> d1 >> m1 >> a1;
    cout << "Ingrese segunda fecha (d m a): ";
    cin >> d2 >> m2 >> a2;

    int f1 = convertirADias(d1,m1,a1);
    int f2 = convertirADias(d2,m2,a2);

    cout << "Días transcurridos: " << abs(f2 - f1) << endl;
    return 0;
}
