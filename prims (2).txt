#include <iostream>
using namespace std;

int main() {
    int V = 5;

    int graph[5][5] = {
        {0, 10, 20, 0, 0},
        {10, 0, 30, 5, 0},
        {20, 30, 0, 15, 6},
        {0, 5, 15, 0, 8},
        {0, 0, 6, 8, 0}
    };

    int selected[5] = {0};
    selected[0] = 1; // Start from first node
    int edges = 0, total = 0;

    cout << "Edge : Weight\n";

    while (edges < V - 1) {
        int min = 999;
        int x = 0, y = 0;

        // Find the minimum edge connecting selected and unselected vertex
        for (int i = 0; i < V; i++) {
            if (selected[i] == 1) {
                for (int j = 0; j < V; j++) {
                    if (selected[j] == 0 && graph[i][j] != 0) {
                        if (graph[i][j] < min) {
                            min = graph[i][j];
                            x = i;
                            y = j;
                        }
                    }
                }
            }
        }

        cout << x << " - " << y << " : " << graph[x][y] << endl;
        total += graph[x][y];
        selected[y] = 1;
        edges++;
    }

    cout << "\nMinimum time to connect all locations (MST Weight) = " << total << endl;

    return 0;
}
