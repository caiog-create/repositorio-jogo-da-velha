# repositorio-jogo-da-velha
#include <stdio.h>

#define TAM 3

// Função para mostrar o tabuleiro
void mostrarTabuleiro(char tabuleiro[TAM][TAM]) {
    printf("\n");
    for (int i = 0; i < TAM; i++) {
        for (int j = 0; j < TAM; j++) {
            printf(" %c ", tabuleiro[i][j]);
            if (j < TAM - 1) printf("|");
        }
        printf("\n");
        if (i < TAM - 1) printf("---+---+---\n");
    }
    printf("\n");
}

int main() {
    char tabuleiro[TAM][TAM];
    int linha, coluna;
    char jogador = 'X'; // Começa com X
    int jogadas = 0;

    // Inicializa o tabuleiro vazio
    for (int i = 0; i < TAM; i++) {
        for (int j = 0; j < TAM; j++) {
            tabuleiro[i][j] = ' ';
        }
    }

    printf("=== JOGO DA VELHA ===\n");

    // Estrutura de rodadas (até preencher o tabuleiro)
    while (jogadas < TAM * TAM) {
        mostrarTabuleiro(tabuleiro);
        printf("Jogador %c, informe linha e coluna (0 a 2): ", jogador);
        scanf("%d %d", &linha, &coluna);

        // Verifica se a posição é válida e está vazia
        while (linha < 0 || linha >= TAM || coluna < 0 || coluna >= TAM || tabuleiro[linha][coluna] != ' ') {
            printf("Posicao invalida ou ocupada! Tente novamente: ");
            scanf("%d %d", &linha, &coluna);
        }

        // Marca a jogada
        tabuleiro[linha][coluna] = jogador;
        jogadas++;

        // Alterna o jogador
        if (jogador == 'X')
            jogador = 'O';
        else
            jogador = 'X';
    }

    // Mostra tabuleiro final
    mostrarTabuleiro(tabuleiro);
    printf("Fim do jogo! (Verificação de vitória será adicionada depois)\n");

    return 0;
}
