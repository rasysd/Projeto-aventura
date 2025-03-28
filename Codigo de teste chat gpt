import random  # Biblioteca para rolagem de dados

def aguardar_tecla():
    """ Aguarda o jogador pressionar Enter antes de continuar. """
    input("\nPRESSIONE ENTER PARA CONTINUAR...")

# Exibir o nome do jogo
aguardar_tecla()  # Aguardar tecla antes de exibir o nome do jogo
print("\n=== COROA AMALDIÇOADA ===\n")

# Função de criação de personagem
def criar_personagem():
    # Pedir o nome do jogador
    nome_jogador = input("Digite seu nome: ")

    # Perguntar o gênero (1 para Masculino, 2 para Feminino)
    genero = input("Escolha seu gênero: 1 - Masculino | 2 - Feminino: ").strip()
    while genero not in ["1", "2"]:
        print("Escolha inválida. Digite 1 para Masculino ou 2 para Feminino.")
        genero = input("Escolha seu gênero: 1 - Masculino | 2 - Feminino: ").strip()

    genero = "Masculino" if genero == "1" else "Feminino"

    # Escolher a classe
    print(f"\nQual a classe do(a) {nome_jogador}?")
    print("1 - Guerreiro")
    print("2 - Patrulheiro")
    print("3 - Paladino")
    print("4 - Mago")
    print("5 - Bruxo")

    classe = input("Escolha um número entre 1 e 5: ")
    while classe not in ["1", "2", "3", "4", "5"]:
        print("Classe inválida! Digite um número entre 1 e 5.")
        classe = input("Escolha um número entre 1 e 5: ")

    # Dicionário para converter a escolha em nome da classe
    classes_dict = {
        "1": "Guerreiro",
        "2": "Patrulheiro",
        "3": "Paladino",
        "4": "Mago",
        "5": "Bruxo"
    }
    classe_nome = classes_dict[classe]

    # Dicionário para atributos principais de cada classe
    atributo_principal_dict = {
        "Guerreiro": "For",
        "Patrulheiro": "Dex",
        "Paladino": "Sab",
        "Mago": "Int",
        "Bruxo": "Car"
    }
    atributo_principal = atributo_principal_dict[classe_nome]

    # Atributos do jogador
    atributos = {
        "For": 0,
        "Dex": 0,
        "Con": 0,
        "Int": 0,
        "Sab": 0,
        "Car": 0
    }

    valores_disponiveis = [17, 15, 14, 12, 10, 8]

    print(f"\nSeu atributo principal como {classe_nome} é {atributo_principal}.")
    print("\nDistribua seus atributos entre os seguintes valores: 17, 15, 14, 12, 10 e 8.")

    for atributo in atributos.keys():
        print(f"\nValores disponíveis: {valores_disponiveis}")
        while True:
            try:
                valor = int(input(f"Escolha um valor para {atributo}: "))
                if valor in valores_disponiveis:
                    atributos[atributo] = valor
                    valores_disponiveis.remove(valor)
                    break
                else:
                    print("Valor inválido! Escolha um dos valores disponíveis.")
            except ValueError:
                print("Digite um número válido.")

    # Exibir resumo do personagem sem mostrar os modificadores
    print("\n=== RESUMO DO PERSONAGEM ===")
    print(f"Nome: {nome_jogador}")
    print(f"Gênero: {genero}")
    print(f"Classe: {classe_nome}")
    print("\nAtributos:")
    for atributo, valor in atributos.items():
        print(f"{atributo}: {valor}")

    return nome_jogador, genero, classe_nome, atributos, atributo_principal


# Criar personagem e retornar os dados
nome_jogador, genero, classe_nome, atributos, atributo_principal = criar_personagem()

# Confirmação antes de iniciar a história
continuar = input("\nDeseja continuar? 1 - Sim | 2 - Não: ")
while continuar not in ["1", "2"]:
    print("Escolha inválida! Digite 1 para continuar ou 2 para refazer o personagem.")
    continuar = input("Deseja continuar? 1 - Sim | 2 - Não: ")

if continuar == "2":
    print("\nReiniciando a criação do personagem...\n")
    nome_jogador, genero, classe_nome, atributos, atributo_principal = criar_personagem()  # Reinicia a criação do personagem

# Introdução ao mundo (você pode modificar esse texto)
print("\nA história começa em um mundo repleto de perigos e mistérios...\n")

# Combate inicial
print("\nVocê se depara com seu primeiro inimigo!\n")

def rolar_d20():
    """ Rola um dado de 20 lados e retorna o resultado. """
    return random.randint(1, 20)

def rolar_d10():
    """ Rola um dado de 10 lados para calcular o dano. """
    return random.randint(1, 10)

# Escolha de ação no combate
print("\nEscolha sua ação:")
print("1 - Atacar")
print("2 - Usar Poção")
print("3 - Fugir")

acao = input("Digite o número da sua ação: ")
while acao not in ["1", "2", "3"]:
    print("Escolha inválida! Digite 1, 2 ou 3.")
    acao = input("Digite o número da sua ação: ")

if acao == "1":  # Atacar
    print(f"\nSeu atributo principal é {atributo_principal}.\n")
    
    # Mostrar os atributos com números associados
    print("\nEscolha um número para o atributo a ser usado no ataque:")
    for i, (atributo, valor) in enumerate(atributos.items(), 1):
        print(f"{i} - {atributo}: {valor}")
    
    # Escolha do atributo pelo número
    escolha = input("Digite o número do atributo para atacar: ")
    while escolha not in ["1", "2", "3", "4", "5", "6"]:
        print("Escolha inválida! Digite um número de 1 a 6.")
        escolha = input("Digite o número do atributo para atacar: ")

    # Mapeamento do número para o nome do atributo
    atributos_lista = list(atributos.keys())
    atributo_escolhido = atributos_lista[int(escolha) - 1]  # Subtrai 1 para acessar o índice correto
    
    print(f"\nVocê escolheu o atributo {atributo_escolhido}.")

    # Rolagem do dado de ataque
    dado_ataque = rolar_d20()
    bonus_ataque = (atributos[atributo_escolhido] - 10) // 2  # Cálculo do bônus: (valor - 10) / 2 arredondado para baixo
    ataque_final = dado_ataque + bonus_ataque
    
    print(f"\nVocê rolou {dado_ataque} + {bonus_ataque} ({atributo_escolhido}). Seu ataque foi {ataque_final}.")

    # Simulação de acerto
    if ataque_final >= 10:  # Vamos assumir que 10 é um número necessário para acertar por enquanto
        print("\nSeu ataque acertou o inimigo!")
        aguardar_tecla()
        
        dado_dano = rolar_d10()
        dano_total = dado_dano + bonus_ataque
        
        print(f"\nDano causado: {dado_dano} + {bonus_ataque} ({atributo_escolhido}) = {dano_total}")
    else:
        print("\nVocê errou o ataque!")

elif acao == "2":  # Usar poção
    print("\nVocê tomou uma poção e restaurou sua energia!")

elif acao == "3":  # Fugir
    print("\nVocê tentou fugir da batalha!")
    
