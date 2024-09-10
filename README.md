
Jogo da Forca

Este é um jogo da forca simples implementado em Python. O objetivo do jogo é adivinhar a palavra secreta letra por letra antes de atingir o limite de erros permitidos. O jogo termina quando o jogador adivinha todas as letras corretamente ou quando a forca é desenhada completamente.

Funções:

1. imprime_mensagem_abertura()
    Exibe uma mensagem de boas-vindas ao usuário quando o jogo começa.

2. jogar()
    Função principal do jogo. Controla o fluxo do jogo, incluindo a exibição da palavra secreta, a solicitação de chutes do jogador, o processamento de chutes corretos e incorretos, e a verificação das condições de vitória e derrota.

3. desenha_forca(erros)
    Desenha a forca com base no número de erros cometidos pelo jogador. O número de erros determina o quão avançada está a figura da forca.

4. imprime_mensagem_vencedor()
    Exibe uma mensagem de vitória e um desenho ASCII quando o jogador vence o jogo.

5. imprime_mensagem_perdedor(palavra_secreta)
    Exibe uma mensagem de derrota e revela a palavra secreta quando o jogador perde o jogo.

6. marca_chute_correto(chute, letras_acertadas, palavra_secreta)
    Atualiza a lista de letras acertadas com base no chute correto do jogador.

7. pede_chute()
    Solicita ao jogador que insira um chute (uma letra) e retorna o valor inserido.

8. inicializa_letras_acertadas(palavra)
    Inicializa a lista de letras acertadas com underscores (_) para representar cada letra da palavra secreta.

9. carrega_palavra_secreta()
    Carrega uma palavra secreta aleatória a partir de um arquivo de texto chamado "palavras.txt". O arquivo deve conter uma lista de palavras, uma por linha.

Notas:
- O arquivo "palavras.txt" deve estar no mesmo diretório que este script para que o jogo funcione corretamente.
- O número máximo de erros permitidos é 7. Após o sétimo erro, o jogo será encerrado como uma derrota.

Exemplo de uso:
Se você executar o script, o jogo será iniciado e as funções serão chamadas conforme necessário para jogar a forca.

```
import random

def imprime_mensagem_abertura():
    """Exibe uma mensagem de boas-vindas ao usuário quando o jogo começa."""
    print("*********************************")
    print("***Bem vindo ao jogo da Forca!***")
    print("*********************************")

def jogar():
    """Função principal do jogo. Controla o fluxo do jogo e gerencia a interação com o jogador."""
    imprime_mensagem_abertura()
    palavra_secreta = carrega_palavra_secreta()

    letras_acertadas = inicializa_letras_acertadas(palavra_secreta)
    print(letras_acertadas)

    enforcou = False
    acertou = False
    erros = 0

    while(not enforcou and not acertou):
        chute = pede_chute()

        if(chute in palavra_secreta):
            marca_chute_correto(chute, letras_acertadas, palavra_secreta)
        else:
            erros += 1
            desenha_forca(erros)

        enforcou = erros == 7
        acertou = "_" not in letras_acertadas

        print(letras_acertadas)

    if(acertou):
        imprime_mensagem_vencedor()
    else:
        imprime_mensagem_perdedor(palavra_secreta)

def desenha_forca(erros):
    """Desenha a forca com base no número de erros cometidos pelo jogador."""
    print("  _______     ")
    print(" |/      |    ")

    if(erros == 1):
        print (" |      (_)   ")
        print (" |            ")
        print (" |            ")
        print (" |            ")

    if(erros == 2):
        print (" |      (_)   ")
        print (" |      \     ")
        print (" |            ")
        print (" |            ")

    if(erros == 3):
        print (" |      (_)   ")
        print (" |      \|    ")
        print (" |            ")
        print (" |            ")

    if(erros == 4):
        print (" |      (_)   ")
        print (" |      \|/   ")
        print (" |            ")
        print (" |            ")

    if(erros == 5):
        print (" |      (_)   ")
        print (" |      \|/   ")
        print (" |       |    ")
        print (" |            ")

    if(erros == 6):
        print (" |      (_)   ")
        print (" |      \|/   ")
        print (" |       |    ")
        print (" |      /     ")

    if (erros == 7):
        print (" |      (_)   ")
        print (" |      \|/   ")
        print (" |       |    ")
        print (" |      / \   ")

    print(" |            ")
    print("_|___         ")
    print()

def imprime_mensagem_vencedor():
    """Exibe uma mensagem de vitória e um desenho ASCII quando o jogador vence o jogo."""
    print("Parabéns, você ganhou!")
    print("       ___________      ")
    print("      '._==_==_=_.'     ")
    print("      .-\\:      /-.    ")
    print("     | (|:.     |) |    ")
    print("      '-|:.     |-'     ")
    print("        \\::.    /      ")
    print("         '::. .'        ")
    print("           ) (          ")
    print("         _.' '._        ")
    print("        '-------'       ")

def imprime_mensagem_perdedor(palavra_secreta):
    """Exibe uma mensagem de derrota e revela a palavra secreta quando o jogador perde o jogo."""
    print("Você foi enforcado!")
    print("A palavra era {}".format(palavra_secreta))
    print("````````````````````````````````````````````````````")
    print("```````````````````$$```````````$$``````````````````")
    print("``````````````````$$$$`````````$$$$`````````````````")
    print("`````````````````$$$$$$```````$$$$$$````````````````")
    print("````````````````$$$$$$$$`````$$$$$$$$```````````````")
    print("```````````````$$$$$$$$$$```$$$$$$$$$$``````````````")
    print("``````````````$$$$$$$$$$$\_/$$$$$$$$$$$`````````````")
    print("``````````````$$$$$$$$$$$$$$$$$$$$$$$$$$````````````")
    print("`````````````$$$$$$`$$$$$$$$$$$$$$`$$$$$````````````")
    print("``$`$```````$$$$$$$```$$$$$$$$$$$``$$$$$$````$``$``$")
    print("``$`$``$````$$$$$$$````$$$$$$$$````$$$$$$`````$`$`$`")
    print("$`$`$`$````$$$$$$$$``````$$$$``````$$$$$$$````$$$$$`")
    print("`$$$$$`````$$$$$$$$```O`$$$$$``O``$$$$$$$$`$$$$$$$``")
    print("`$$$$$$$$``$$$$$$$$$````$$$$$$````$$$$$$$$$$```$$$``")
    print("````$$````$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$`$$````$$``")
    print("````$`````$$$`$$$$$$$$$$$$$$$$$$$$$$$$$$``$$````````")
    print("``````````$$$``$$$$$$$$$$$$$$$$$$$$$$$$``$$$````````")
    print("``````````$$$``$$$$$$$$$$$$$$$$$$$$$$$$``$$$````````")
    print("```````````$$$`````$$$$$$$$$$$$$$$$`````$$``````````")
    print("````````````$$````````$$$$$$$$$$```````$$```````````")
    print("`````````````$$$``````$$$````$$$```````$````````````")
    print("```````````````$$`````$$``````$$``````$`````````````")
    print("````````````````$$$```$````````$`````$``````````````")
    print("```````````````````$$$``````````````$```````````````")
    print("``````````````````````$$$$$$$$$$$$$````````````````")

def marca_chute_correto(chute, letras_acertadas, palavra_secreta):
    """Atualiza a lista de letras acertadas com base no chute correto do jogador."""
