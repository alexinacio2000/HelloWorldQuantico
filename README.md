# 💡 Introdução ao Q# – Hello World da Computação Quântica  

Este repositório contém um exemplo básico de um **Hello World** em **Q#**, a linguagem da **Microsoft** para computação quântica. O código implementa um par **entrelaçado** de qubits usando **portas quânticas Hadamard (H) e CNOT**, rodando no **Azure Quantum Development Kit**.  

## 🚀 Requisitos  

Antes de rodar o código, é necessário configurar o ambiente com o **Quantum Development Kit (QDK)** da Microsoft.  

### 🛠️ Instalação do QDK  

1️⃣ **Instale o .NET SDK**  
O Q# é executado sobre a plataforma .NET. Primeiro, instale o .NET SDK, caso ainda não tenha:  

🔗 [Download do .NET SDK](https://dotnet.microsoft.com/en-us/download)  

2️⃣ **Instale o Quantum Development Kit (QDK)**  
Agora, instale o QDK via terminal:  

```sh
dotnet new install Microsoft.Quantum.ProjectTemplates
```

3️⃣ **Verifique a instalação**  
Para garantir que tudo foi instalado corretamente, rode o seguinte comando:  

```sh
dotnet --list-sdks
```

Se o .NET e o QDK estiverem instalados corretamente, você verá a versão do SDK listada.  

---

## 📌 Como Executar o Código  

1️⃣ **Crie um novo projeto Q#**  
Caso queira criar um novo projeto do zero, use:  

```sh
dotnet new console -lang Q# -o MeuProjetoQSharp
cd MeuProjetoQSharp
```

2️⃣ **Adicione o código ao arquivo `Program.qs`**  

Abra o arquivo `Program.qs` e substitua o conteúdo pelo código abaixo:  

```qsharp
import Microsoft.Quantum.Diagnostics::*;

operation Main(): (Result, Result){
    use(q1,q2) = (Qubit(),Qubit());
    H(q1);
    CNOT(q1, q2);
    DumpMachine();
    let (m1, m2) = (M(q1), M(q2));
    Reset(q1);
    Reset(q2);
    return (m1, m2);
}
```

3️⃣ **Compile e execute o código**  

No terminal, rode o seguinte comando para executar a simulação:  

```sh
dotnet run
```

---

## 📊 O que este código faz?  

O código cria **dois qubits entrelaçados** e os mede. O resultado esperado é um estado **de Bell**, onde os qubits estarão sempre correlacionados:  

- Se **q1 for 0**, **q2 também será 0**  
- Se **q1 for 1**, **q2 também será 1**  

Saída esperada da simulação:  

```
Basis | Amplitude       | Probability | Phase  
------------------------------------------------  
|00⟩   | 0.7071+0.0000i | 50.0000%    | 0.0000  
|11⟩   | 0.7071+0.0000i | 50.0000%    | 0.0000  

(Zero, Zero)  
Finished shot 1 of 1  
Q# simulation completed.  
```

---

## 🧑‍💻 Recursos úteis  

🔹 **Documentação do QDK:** [Microsoft Quantum Documentation](https://learn.microsoft.com/en-us/azure/quantum/)  
🔹 **Q# no VS Code:** [QDK Extension](https://marketplace.visualstudio.com/items?itemName=quantum.microsoft)  
🔹 **Tutoriais Microsoft Quantum:** [Quantum Learning](https://learn.microsoft.com/en-us/azure/quantum/user-guide-qdk-overview)  

---

🚀 **Agora é só rodar o código e começar a explorar o mundo da computação quântica!** Se tiver dúvidas, sinta-se à vontade para abrir uma issue. 😊
