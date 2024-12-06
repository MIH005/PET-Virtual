# 🐾 **Simulador de Animal de Estimação Virtual** 🐾

Bem-vindo ao **Simulador de Animal de Estimação Virtual**! 🐶🐱 Neste jogo, você poderá cuidar do seu próprio pet virtual enquanto aprende sobre **programação orientada a objetos**. Cuide do seu pet, faça-o feliz e saudável, e leve-o até a idade de 50 anos!

## 🧸 **Funcionalidades do Projeto**:

### 🐾 **Atributos do Pet**:
- **Nome**: O nome do pet.
- **Nível de Fome**: Representa o quanto o pet está com fome. Quanto maior, mais fome!
- **Nível de Felicidade**: O quão feliz o pet está. Quanto maior, mais feliz!
- **Nível de Cansaço**: Representa o quão cansado o pet está. Quanto maior, mais cansado.
- **Idade**: A idade do pet, que aumenta com o tempo.
- **Vontade de Ir ao Banheiro**: Aumenta quando o pet se alimenta.
- **Sujeira**: Aumenta quando o pet brinca.

### 🐾 **Métodos do Pet**:
- **Alimentar**: Diminui o nível de fome e aumenta a vontade de ir ao banheiro.
- **Brincar**: Aumenta a felicidade, o cansaço e a sujeira do pet.
- **Descansar**: Diminui o cansaço do pet.
- **Passar Tempo**: Simula o passar do tempo, fazendo o pet envelhecer e alterando seus atributos.
- **Verificar Status**: Exibe o status atual do pet (nome, fome, felicidade, cansaço, idade, etc.).

### 🐾 **Regras do Jogo**:
- O objetivo do jogo é levar o pet até **50 anos de idade**.
- Se o pet atingir o nível máximo de **fome** (100), **felicidade** (0), **cansaço** (100), **vontade de ir ao banheiro** (100) ou **sujeira** (100), o jogador perde o jogo.
- O jogador precisa gerenciar os cuidados com o pet para evitar a perda do jogo.

## ⚙️ **Como Executar**:

1. **Clone o repositório**:
   ```bash
   git clone https://github.com/seu-usuario/simulador-pet.git
   ```

2. **Compile o código Java**:
   Navegue até o diretório onde o arquivo `SimuladorPet.java` está localizado e compile o código:
   ```bash
   javac SimuladorPet.java
   ```

3. **Execute o programa**:
   Após a compilação, execute o programa com o comando:
   ```bash
   java SimuladorPet
   ```

4. **Interaja com o seu Pet**:
   O programa solicitará um nome para o pet e permitirá que você interaja com ele através de um menu com várias opções: alimentar, brincar, descansar, verificar status e passar o tempo.

## 🎮 **Como Jogar**:

### 🐾 **Menu de Ações**:
1. **Alimentar**: Diminui o nível de fome do pet.
2. **Brincar**: Aumenta a felicidade do pet, mas também aumenta o cansaço e a sujeira.
3. **Descansar**: Reduz o nível de cansaço do pet.
4. **Verificar Status**: Exibe o status atual do pet (fome, felicidade, cansaço, etc.).
5. **Passar Tempo**: Simula o passar do tempo, envelhecendo o pet e alterando seus atributos.
6. **Sair**: Encerra o jogo.

### ⚖️ **Regras**:
- O objetivo é atingir **50 anos de idade** do pet.
- O jogo termina se o pet atingir **fome = 100**, **felicidade = 0**, **cansaço = 100**, **sujeira = 100** ou **vontade de ir ao banheiro = 100**.
  
## 🐱 **Código-fonte**:

### 📜 **SimuladorPet.java**
```java
import java.util.Scanner;

class Pet {
    String nome;
    int nivelFome;
    int nivelFelicidade;
    int nivelCansaco;
    int idade;
    int vontadeIrAoBanheiro;
    int sujeira;

    // Construtor
    public Pet(String nome) {
        this.nome = nome;
        this.nivelFome = 50;   // Começa com fome média
        this.nivelFelicidade = 50;  // Começa com felicidade média
        this.nivelCansaco = 0;  // Começa descansado
        this.idade = 0;
        this.vontadeIrAoBanheiro = 0;
        this.sujeira = 0;
    }

    // Métodos de ação
    public void alimentar(int quantidade) {
        if (quantidade > 0) {
            this.nivelFome -= quantidade;
            if (this.nivelFome < 0) this.nivelFome = 0;
            this.vontadeIrAoBanheiro += 5;  // Alimentação aumenta a vontade de ir ao banheiro
            System.out.println(nome + " foi alimentado!");
        } else {
            System.out.println("Operação não autorizada! A quantidade deve ser positiva.");
        }
    }

    public void brincar(int quantidade) {
        if (quantidade > 0) {
            this.nivelFelicidade += quantidade;
            this.sujeira += 5;  // Brincar aumenta a sujeira
            this.nivelCansaco += 10;  // Brincar aumenta o cansaço
            System.out.println(nome + " se divertiu brincando!");
        } else {
            System.out.println("Operação não autorizada! A quantidade deve ser positiva.");
        }
    }

    public void descansar(int horas) {
        if (horas > 0) {
            this.nivelCansaco -= horas;
            if (this.nivelCansaco < 0) this.nivelCansaco = 0;
            System.out.println(nome + " descansou por " + horas + " horas.");
        } else {
            System.out.println("Operação não autorizada! O tempo de descanso deve ser positivo.");
        }
    }

    public void passarTempo() {
        this.nivelFome += 3;
        this.nivelFelicidade -= 3;
        this.idade++;
        this.nivelCansaco += 10;
        this.vontadeIrAoBanheiro += 5;
        this.sujeira += 5;

        // Verificar se o pet perdeu o jogo
        if (this.nivelFome >= 100 || this.nivelFelicidade <= 0 || this.nivelCansaco >= 100 || this.vontadeIrAoBanheiro >= 100 || this.sujeira >= 100) {
            System.out.println(nome + " perdeu o jogo!");
            System.exit(0);
        }
    }

    public void verificarStatus() {
        System.out.println("Status do Pet:");
        System.out.println("Nome: " + nome);
        System.out.println("Fome: " + nivelFome);
        System.out.println("Felicidade: " + nivelFelicidade);
        System.out.println("Cansaço: " + nivelCansaco);
        System.out.println("Idade: " + idade);
        System.out.println("Vontade de ir ao banheiro: " + vontadeIrAoBanheiro);
        System.out.println("Sujeira: " + sujeira);
    }
}

public class SimuladorPet {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Nome do Pet
        System.out.print("Qual nome você daria ao seu Pet? ");
        String nomePet = scanner.nextLine();
        
        // Criar Pet
        Pet pet = new Pet(nomePet);

        // Loop do Jogo
        while (true) {
            // Exibir Menu
            System.out.println("\n--- Menu ---");
            System.out.println("1. Alimentar");
            System.out.println("2. Brincar");
            System.out.println("3. Descansar");
            System.out.println("4. Verificar Status");
            System.out.println("5. Passar Tempo");
            System.out.println("6. Sair");
            System.out.print("Escolha uma opção: ");
            int opcao = scanner.nextInt();
            
            // Validar senha para ações sensíveis
            System.out.print("Informe a senha: ");
            int senha = scanner.nextInt();
            if (senha != 3589) {
                System.out.println("Senha incorreta! Tente novamente.");
                continue;
            }

            // Processar opção
            switch (opcao) {
                case 1:
                    System.out.print("Quanto você quer alimentar o Pet? ");
                    int quantidadeAlimentacao = scanner.nextInt();
                    pet.alimentar(quantidadeAlimentacao);
                    break;
                case 2:
                    System.out.print("Quanto você quer brincar com o Pet? ");
                    int quantidadeBrincar = scanner.nextInt();
                    pet.brincar(quantidadeBrincar);
                    break;
                case 3:
                    System.out.print("Por quant

as horas o Pet vai descansar? ");
                    int horasDescanso = scanner.nextInt();
                    pet.descansar(horasDescanso);
                    break;
                case 4:
                    pet.verificarStatus();
                    break;
                case 5:
                    pet.passarTempo();
                    System.out.println("Tempo passou...");
                    break;
                case 6:
                    System.out.println("Obrigado por jogar! Até a próxima.");
                    System.exit(0);
                    break;
                default:
                    System.out.println("Opção inválida! Tente novamente.");
                    break;
            }
        }
    }
}
```
