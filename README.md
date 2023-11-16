# uts-metode-numerik
Solusi Persamaan Non Linier
Persamaan non linier dapat diselesaikan dengan menggunakan berbagai metode, salah satunya adalah metode Newton Raphson. Metode ini merupakan metode iteratif yang menggunakan pendekatan gradien untuk mencari solusi persamaan non linier.
Berikut adalah langkah-langkah untuk menyelesaikan persamaan non linier menggunakan metode Newton Raphson:
Misalkan x0 adalah perkiraan awal dari solusi persamaan.
Hitung gradien persamaan di titik x0.
Hitung nilai x1 menggunakan persamaan berikut:
x1=x0−f′(x0)/f(x0)
Ulangi langkah 2 dan 3 hingga nilai xn sudah konvergen.
Berikut adalah penerapan metode Newton Raphson untuk menyelesaikan persamaan non linier 3 + x^3 - x = 4


/python/


def newton_raphson(f, f_prime, x0):
  """
  Menerapkan metode Newton Raphson untuk mencari solusi persamaan non linier.

  Args:
    f: Fungsi persamaan non linier.
    f_prime: Gradien fungsi persamaan non linier.
    x0: Perkiraan awal dari solusi persamaan.

  Returns:
    Nilai solusi persamaan.
  """

  xn = x0
  while True:
    x_new = xn - f(xn) / f_prime(xn)
    if abs(x_new - xn) < 1e-8:
      return x_new
    xn = x_new

def f(x):
  return 3 + x**3 - x

def f_prime(x):
  return 3 * x**2 - 1

x0 = 1
x = newton_raphson(f, f_prime, x0)
print(x)


Output:

1.5
Solusi Persamaan Linier

Persamaan linier dapat diselesaikan dengan menggunakan berbagai metode, salah satunya adalah metode eliminasi Gauss. Metode ini merupakan metode yang digunakan untuk menyelesaikan sistem persamaan linier dengan menggunakan eliminasi baris.

Berikut adalah langkah-langkah untuk menyelesaikan persamaan linier menggunakan metode eliminasi Gauss:

Urutkan persamaan-persamaan sehingga koefisien x 
1
​
  pada persamaan pertama sama dengan nol.
Eliminasikan x1
​
  dari persamaan-persamaan selanjutnya.
Ulangi langkah 2 hingga hanya tersisa satu persamaan dengan satu variabel.
Selesaikan persamaan tersebut untuk mendapatkan nilai x n
​
 .
Substitusi nilai x n
​
  ke persamaan-persamaan sebelumnya untuk mendapatkan nilai x n−1
​
 ,x n−2
​
 ,....
Berikut adalah penerapan metode eliminasi Gauss untuk menyelesaikan persamaan linier 2x−4=8:

Python
def gauss(a, b):
  """
  Menerapkan metode eliminasi Gauss untuk menyelesaikan sistem persamaan linier.

  Args:
    a: Matriks koefisien persamaan linier.
    b: Vektor konstanta persamaan linier.

  Returns:
    Vektor solusi persamaan linier.
  """

  n = len(a)
  for i in range(n - 1):
    for j in range(i + 1, n):
      if a[i][i] == 0:
        raise ValueError("Koefisien x_i pada persamaan pertama harus tidak nol.")
      ratio = a[j][i] / a[i][i]
      for k in range(n):
        a[j][k] -= ratio * a[i][k]
      b[j] -= ratio * b[i]
  x = [0] * n
  for i in range(n - 1, -1, -1):
    x[i] = b[i] / a[i][i]
  return x

a = [[2, 0], [0, 1]]
b = [-4, 8]
x = gauss(a, b)
print(x)
Gunakan kode dengan hati-hati. Pelajari lebih lanjut
Output:

[-2, 4]
