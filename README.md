#include <iostream>
using   std::cin;
using   std::cout;
using   std::endl;

#define task9

#ifdef task1
int main()
{
    const int n = 10;
    int arr[n];
    int poloj[n], otric[n];
    int kolvo_p = 0, kolvo_o = 0;

    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    for (int i = 0; i < n; i++) {
        if (arr[i] > 0) {
            poloj[kolvo_p] = arr[i];
            kolvo_p = kolvo_p + 1;
        }
        else if (arr[i] < 0) {
            otric[kolvo_o] = arr[i];
            kolvo_o++;
        }
    }

    for (int i = 0; i < kolvo_p; i++) {
        cout << poloj[i] << " ";
    }
    cout << endl;

    for (int i = 0; i < kolvo_o; i++) {
        cout << otric[i] << " ";
    }
}
#endif

#ifdef task2
int main() {
    const int n = 10;
    int mas[n];

    for (int i = 0; i < n; i++) {
        cin >> mas[i];
    }

    for (int i = 0; i < n - 1; i++) {
        if (mas[i] > 0 && mas[i + 1] > 0) {
            cout << mas[i] << " " << mas[i + 1] << endl;
        }
        if (mas[i] < 0 && mas[i + 1] < 0) {
            cout << mas[i] << " " << mas[i + 1] << endl;
        }
    }
}
#endif

#ifdef task3
int main() {
    const int n = 10;
    int chisla[n];

    for (int i = 0; i < n; i++) {
        cin >> chisla[i];
    }

    int samaya_dlinnaya = 0;
    int tekushaya = 0;

    for (int i = 0; i < n; i++) {
        if (chisla[i] % 2 == 0) {
            tekushaya = tekushaya + 1;
        }
        else {
            if (tekushaya > samaya_dlinnaya) {
                samaya_dlinnaya = tekushaya;
            }
            tekushaya = 0;
        }
    }

    if (tekushaya > samaya_dlinnaya) {
        samaya_dlinnaya = tekushaya;
    }

    cout << samaya_dlinnaya;
}
#endif

#ifdef task4
int main() {
    const int n = 10;
    int a[n];

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    int gde_max = 0;
    for (int i = 1; i < n; i++) {
        if (a[i] > a[gde_max]) {
            gde_max = i;
        }
    }

    for (int i = gde_max + 1; i < n; i++) {
        a[i] = 1;
    }

    for (int i = 0; i < n; i++) {
        cout << a[i];
        if (i != n - 1) cout << " ";
    }
}
#endif

#ifdef task5
int main() {
    const int n = 10;
    int b[n];

    for (int i = 0; i < n; i++) {
        cin >> b[i];
    }

    // 1
    int chet = 0, nechet = 0;
    for (int i = 0; i < n; i++) {
        if (b[i] % 2 == 0) chet++;
        else nechet++;
    }
    cout << chet << " " << nechet << endl;

    // 2
    int summa = 0;
    for (int i = 0; i < n; i++) {
        if (b[i] % 3 == 0) {
            summa = summa + b[i];
        }
    }
    cout << summa << endl;

    // 3
    int skolko = 0;
    int pervie = b[0];
    for (int i = 0; i < n; i++) {
        if (b[i] % pervie == 0) {
            skolko = skolko + 1;
        }
    }
    cout << skolko << endl;

    // 4
    int luchshee_chislo = b[0];
    int skolko_delitelei_max = 0;

    for (int i = 0; i < n; i++) {
        int skolko_delitelei = 0;
        for (int delitel = 1; delitel <= b[i]; delitel++) {
            if (b[i] % delitel == 0) {
                skolko_delitelei++;
            }
        }
        if (skolko_delitelei > skolko_delitelei_max) {
            skolko_delitelei_max = skolko_delitelei;
            luchshee_chislo = b[i];
        }
    }
    cout << luchshee_chislo << endl;

    // 5
    int summa_vseh = 0;
    for (int i = 0; i < n; i++) {
        summa_vseh += b[i];
    }
    int srednee_znachenie = summa_vseh / n;

    int nashli = 0;
    for (int i = 0; i < n; i++) {
        if (b[i] % 2 == 1) {
            if (b[i] % 5 == 0) {
                if (b[i] > srednee_znachenie) {
                    nashli = 1;
                    break;
                }
            }
        }
    }

    if (nashli == 1) cout << "yes";
    else cout << "no";
}
#endif

#ifdef task6
int main() {
    int n;
    cin >> n;
    int c[n];

    for (int i = 0; i < n; i++) {
        cin >> c[i];
    }

    int dlina = 1;
    int nachalo = 0;
    int tek_dlina = 1;
    int tek_nachalo = 0;

    for (int i = 1; i < n; i++) {
        int raznica = c[i] - c[i - 1];

        if (i == 1) {
            if (raznica != 0) {
                tek_dlina = 2;
            }
            continue;
        }

        int pred_raznica = c[i - 1] - c[i - 2];

        if (raznica == 0) {
            tek_dlina = 1;
            tek_nachalo = i;
        }
        else if (pred_raznica > 0 && raznica < 0) {
            tek_dlina++;
        }
        else if (pred_raznica < 0 && raznica > 0) {
            tek_dlina++;
        }
        else {
            tek_dlina = 2;
            tek_nachalo = i - 1;
        }

        if (tek_dlina > dlina) {
            dlina = tek_dlina;
            nachalo = tek_nachalo;
        }
    }

    cout << dlina << " " << nachalo;
}
#endif

#ifdef task7
int main() {
    int n, k;
    cin >> n >> k;
    int d[n];

    for (int i = 0; i < n; i++) {
        cin >> d[i];
    }

    // 1
    int ostatki[k];
    for (int i = 0; i < k; i++) {
        ostatki[i] = 0;
    }

    for (int i = 0; i < n; i++) {
        int ost = d[i] % k;
        if (ost < 0) ost = ost + k;
        ostatki[ost]++;
    }

    for (int i = 0; i < k; i++) {
        cout << ostatki[i] << " ";
    }
    cout << endl;

    // 2
    int max_podryad = 1;
    int start_index = 0;
    int end_index = 0;
    int tek_podryad = 1;
    int tek_start = 0;

    for (int i = 1; i < n; i++) {
        int ost1 = d[i] % k;
        int ost2 = d[i - 1] % k;
        if (ost1 < 0) ost1 += k;
        if (ost2 < 0) ost2 += k;

        if (ost1 == ost2) {
            tek_podryad++;
            if (tek_podryad > max_podryad) {
                max_podryad = tek_podryad;
                start_index = tek_start;
                end_index = i;
            }
        }
        else {
            tek_podryad = 1;
            tek_start = i;
        }
    }

    cout << max_podryad << " " << start_index << " " << end_index << endl;

    // 3
    int noviy[n];
    int poziciya = 0;

    for (int ost = 0; ost < k; ost++) {
        for (int i = 0; i < n; i++) {
            int tek_ost = d[i] % k;
            if (tek_ost < 0) tek_ost += k;
            if (tek_ost == ost) {
                noviy[poziciya] = d[i];
                poziciya++;
            }
        }
    }

    for (int i = 0; i < n; i++) {
        cout << noviy[i] << " ";
    }
    cout << endl;

    // 4
    int delitel1 = 0, delitel2 = 0;
    for (int i = 2; i < k; i++) {
        if (k % i == 0) {
            if (delitel1 == 0) {
                delitel1 = i;
            }
            else if (delitel2 == 0) {
                delitel2 = i;
                break;
            }
        }
    }

    int resultat = -1;
    if (delitel1 > 0 && delitel2 > 0) {
        for (int i = 0; i < n; i++) {
            if (d[i] % delitel1 == 0 && d[i] % delitel2 == 0) {
                resultat = d[i];
                break;
            }
        }
    }

    if (resultat != -1) {
        cout << resultat;
    }
    else {
        cout << "net";
    }
}
#endif

#ifdef task8
int NOD(int x, int y) {
    while (y != 0) {
        int temp = y;
        y = x % y;
        x = temp;
    }
    return x;
}

int main() {
    int n;
    cin >> n;
    int e[n];

    for (int i = 0; i < n; i++) {
        cin >> e[i];
    }

    // 1
    int para_sosed = 0;
    for (int i = 0; i < n - 1; i++) {
        if (NOD(e[i], e[i + 1]) == 1) {
            para_sosed++;
        }
    }
    cout << para_sosed << endl;

    // 2
    int max_proizv = -1;
    int chislo1, chislo2;
    int est_para = 0;

    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (NOD(e[i], e[j]) == 1) {
                int proizv = e[i] * e[j];
                if (proizv > max_proizv) {
                    max_proizv = proizv;
                    chislo1 = e[i];
                    chislo2 = e[j];
                    est_para = 1;
                }
            }
        }
    }

    if (est_para) {
        cout << chislo1 << " " << chislo2 << endl;
    }
    else {
        cout << "net" << endl;
    }

    // 3
    int naydeno_troek = 0;
    for (int i = 0; i < n - 2; i++) {
        int x = e[i], y = e[i + 1], z = e[i + 2];
        if (NOD(x, y) == 1 && NOD(y, z) == 1) {
            if ((x + z) % y == 0) {
                cout << x << " " << y << " " << z << " " << i << " " << i + 1 << " " << i + 2 << endl;
                naydeno_troek = 1;
                break;
            }
        }
    }

    if (!naydeno_troek) {
        cout << "net" << endl;
    }

    // 4
    int massiv[n];
    for (int i = 0; i < n; i++) {
        int est_svyaz = 0;
        for (int j = 0; j < n; j++) {
            if (i != j) {
                if (e[i] % e[j] == 0 || e[j] % e[i] == 0) {
                    est_svyaz = 1;
                    break;
                }
            }
        }
        massiv[i] = est_svyaz;
    }

    int summa_massiva = 0;
    for (int i = 0; i < n; i++) {
        cout << massiv[i] << " ";
        summa_massiva += massiv[i];
    }
    cout << endl << summa_massiva;
}
#endif

#ifdef task9
int main() {
    int matrix[4][4];

    // ввод
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cin >> matrix[i][j];
        }
    }

    // 1
    int skalyar;
    cin >> skalyar;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << matrix[i][j] * skalyar << " ";
        }
        cout << endl;
    }

    // 2
    for (int i = 0; i < 4; i++) {
        int summa_stroki = 0;
        for (int j = 0; j < 4; j++) {
            summa_stroki += matrix[i][j];
        }
        cout << summa_stroki << " ";
    }
    cout << endl;

    for (int j = 0; j < 4; j++) {
        int summa_stolbca = 0;
        for (int i = 0; i < 4; i++) {
            summa_stolbca += matrix[i][j];
        }
        cout << summa_stolbca << " ";
    }
    cout << endl;

    // 3
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            if (matrix[i][j] < 0) {
                cout << "10 ";
            }
            else {
                cout << matrix[i][j] << " ";
            }
        }
        cout << endl;
    }

    // 4
    int minimum = matrix[0][0];
    int maximum = matrix[0][0];
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            if (matrix[i][j] < minimum) minimum = matrix[i][j];
            if (matrix[i][j] > maximum) maximum = matrix[i][j];
        }
    }
    cout << minimum << " " << maximum << endl;

    // 5
    int matrix2[4][4];
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cin >> matrix2[i][j];
        }
    }

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << matrix[i][j] + matrix2[i][j] << " ";
        }
        cout << endl;
    }

    // 6
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            if (matrix[i][j] == matrix2[i][j]) {
                cout << "1 ";
            }
            else {
                cout << "0 ";
            }
        }
        cout << endl;
    }
}
#endif
