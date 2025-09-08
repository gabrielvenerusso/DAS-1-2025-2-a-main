Turma: das-1-2025-2-a
Aula 1 - 04/08/2025 !!
Principios de projeto de software - Capitulo 5 do livro

Padrões mitigam a complexidade

Abstração:
Seria representar algo do mundo real para resolver um problema

Config <-- configurações

Controller <-- html, api, rest

Entity <-- dados

Repository <-- Con db

Service <-- Lógica

Ocultamento de informação:
Não há necessidade de entender todo o funcionamento de um framework para poder usa-lo

Código Coeso (Coesão)
Um código que realiza uma tarefa muito bem feita! Elementos de um módulo (como classes, funções ou pacotes) estão relacionados e trabalham juntos para um propósito único e bem definido.

Acoplamento
Acoplamento: dependência de uma classe com outra
Autoacoplamento: instanciação e uso de um método no construtor de outra class
UML

Flecha vazia: herança
Flecha tracejada: implementação
Flecha cheia: Associação
---//---

Aula 2 - 05/08/2025 !!
O que é SOLID?

Usar a orientação a objetos do jeito mais correto possível!

S — Single Responsibility Principle (Princípio da responsabilidade única) O — Open-Closed Principle (Princípio Aberto-Fechado) L — Liskov Substitution Principle (Princípio da substituição de Liskov) I — Interface Segregation Principle (Princípio da Segregação da Interface) D — Dependency Inversion Principle (Princípio da inversão da dependência)

Maneira de usar o conceito de responsábildiade única M - Dados V - HTML C - Controlar a tela

package br.univille;

import javax.swing.JButton; import javax.swing.JFrame;

public class Janelinha extends JFrame {

private JButton botaozinho;
private Controlador controlador;

public Janelinha() {
    setTitle("Eu não acredito");
    setSize(500, 500);
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    botaozinho = new JButton("ME CLICA");
    controlador = new Controlador();
    botaozinho.addActionListener(controlador);

    add(botaozinho);

    setVisible(true);
}

public static void main(String[] args) {
    new Janelinha();
}
package br.univille;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JOptionPane;

public class Controlador implements ActionListener {

@Override
public void actionPerformed(ActionEvent e) {
    meClica();
}

private void meClica() {
    JOptionPane.showMessageDialog(null, "NÃO ACREDITO");
}
}
---//---

Aula 3 - 11/08/2025 !!
#Princípio da Inversão de Dependência (Dependency Inversion Principle) Em vez de o Controller depender diretamente de uma implementação concreta, ele deve se comunicar primeiro com uma interface ou abstração. Isso evita o acoplamento direto entre classes, facilitando a manutenção, a troca de implementações e a realização de testes. A ideia central é: módulos de alto nível não devem depender de módulos de baixo nível, ambos devem depender de abstrações.

Prefira Composição à Herança
A herança deve ser usada apenas quando existe uma relação clara do tipo "é um" (is-a), por exemplo:

Animal → Gato

Animal → Cachorro

Um gato nunca se tornará um cachorro, ou vice-versa. Quando a relação não for estritamente hierárquica, prefira composição, ou seja, construir comportamentos combinando diferentes objetos, em vez de criar cadeias de herança profundas.

A composição oferece mais flexibilidade, evita acoplamento excessivo e facilita a reutilização de código.

--//--

Princípio de Demeter (Menor Conhecimento)
Também chamado de Law of Demeter.

A ideia é evitar dependências desnecessárias e não acessar diretamente objetos internos de outros objetos. Fuja de variáveis globais e trabalhe com as informações locais e disponíveis no contexto atual.

--//--

Princípio do Aberto/Fechado (Open/Closed Principle)
Um objeto deve proteger seu comportamento para que ninguém possa quebrá-lo alterando diretamente sua lógica interna. A ideia é que quem cria a classe não quer que ela seja modificada, mas sim estendida com novas funcionalidades.

Aberto para extensão, fechado para modificação Proteja o que a classe já faz, mas permita adicionar novos comportamentos sem alterar o código existente.

Aula 4 - 12/08/2025
SOLID:

L: Princípio de substituição de Liskov - redefinição de métodos de classe base em classe filho (aplicado quando tem herança). Se há uma herança, com vários filhos, o código dos filhos deve ser feita de tal maneira a manter a compatibilidade com o pai, caso elas forem substituídas (sem quebrar o padrão que o pai tem) Filho(método x) -> Pai <- Filho2(Método x) | aplicar os dois filhos não quebra a classe


Aula 5 - 26/08/2025 Fundamentos da Arquitetura de Software

Caracteristicas da Arquitetura = requisitos não funcionais Disponibilidade - estar online por um tempo definido Confiabiliade - o sistema faz o que deve ser feito Segurança - quão seguro o sistema é (cada CPF vazado é no mínimo 50 mil de multa) Testabilidade Escalabildade Agilidade Tolerância a falhas Elasticidade Recuperabilidade Desempenho Implementabilidade Capacidade de aprendizagem

É impossível um sistema atender todas as caracnteristicas da arquitetura, sempre ficará alguma coisa pendente

Supply chain - utilização de bliblioteca abertas não confiáveis

DECISÕES DA ARQUITETURA São regras que precisam ser mantidas no sistema, para que o mesmo tenha o mínimo de padronização. exemplo: iremos utilizar arquitetura baseada em camadas.

Decidir a esturutra do sistema, escolhendo a arquitetura, uma decisão importante, que poderá ter um custo alto se feito de qualquer jeito

A decisão da arquitetura depende das caracteristicas da arquitetura, um depende do outro

PRINCÍPIOS DO DESIGN Boas práticas, princípios que seria ideal sempre ser seguido

(arquitetura distribuida) - micro serviços - pequenas atividades bem feitas, cada micro serviço tem seu próprio banco de dados (cada um tem vida própria)

sistema de mensageria - serviço colocado no meio da arquitetura, que permite a troca de mensagens dos micros serviços, um manda mensagem e o outro recebe

event driven architecture - arquitetura baseada em eventos (alexa - cria máquina virtual, responde a pergunta, e cai a máquina virtual)

Aula 6 - 01/09/2025

EXPECTATIVAS DO ARQUITETO

Tomar decisões de arquitetura - decidir qual arquitetura/ estrutura será utilizada no sistema, utilizando sua experiência no mercado para orientar a sua equipe. "O segredo para tomar decisões arquiteturais eficientes é perguntar se a decisão da arquitetura está ajudando a orientar as equipes ao fazerem a escolha técnica certa ou se a decisão faz a escolha técnica por elas."

Analisar continuamente a arquitetura - todo sistema muda com o tempo, com isso, é função do arquiteto analisar o sistema continuamente e atualizar de acorodo com a arquitetura do sistema. O famoso "não mexe, que está funcionando", não deve ser considerado, e sim tomar decições corretas de acordo com suas análises que facilitarão o sistema

Manter-se atualizando com as últimas tendências - desenvolver software está cada vez mais complexo (Inteligência Artificial)

Assegurar a conformidade com as decisões - o arquiteto verifica continuamente se as equipes de desenvolvimento seguem as decisões da arquitetura e os princípios do design definidos, documentados e comunicados por ele.

Análise estática de código é a inspeção do código-fonte de um software sem executá-lo, utilizando ferramentas automatizadas para identificar bugs, vulnerabilidades de segurança e desvios de padrões de codificação antes da produção

Exposição e experiência diverisades - um bom arquiteto já teve experiência em várias áreaa/funções e linguagens. Essencial ele ter conhecimento da regra de negócio do produto

Ter conhecimento sobre o domínio do negócio -

Ter habilidades interpessoais - um arquiteto precisa ser um gestor tambémm, um líder da equipe, incetivando e extaindo o melhor de cada membro da equipe

Enteder e lidarr bem com questões políticas - fundamental negociar com o cliente, negociar mais prazos, funcionalidades, influenciar e proteger sua equipe

DEADLOCK - (ou interbloqueio) é uma situação de impasse em computação onde dois ou mais processos ficam permanentemente bloqueados, cada um esperando que o outro libere um recurso que ele precisa para continuar sua execução. Isso cria uma espera circular, onde o Processo A espera por um recurso do Processo B, e o Processo B espera por um recurso do Processo A, impedindo que qualquer um deles avance.

OPERAÇÕES - DevOps uma maneira de entregar valor ao meu cliente mais rápido metodologia que vai melhorando cada vez mais

Aula 7 - 02/09/2025

Resuma a diferença entre arquitetura e design ? A arquitetura de software define a estrutura global e os componentes principais de um sistema, ou seja, o que terá no sistema, enquanto o design se concentra nos detalhes de implementação desses componentes e suas interações em um nível mais baixo, ou seja, como será implamentado as decisões tomada pelo arquiteto. A arquitetura é uma visão de alto nível que garante requisitos globais como escalabilidade e segurança, enquanto o design detalha como cada parte do sistema funciona e se comunica.

Como é a formação do conhecimento de um arquiteto modelo T? Uma formação ampla, não se concentra em apenas uma linguagem ou área específica de trabalho. O arquieto tem a capacidade de resolver o mesmo problema, utilizando meios diferentes.

