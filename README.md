# Projetos AC Partners

Apresentação de dois sistemas que desenvolvi para a **AC Partners**, uma fábrica de injeção de plásticos. **O código é privado e propriedade da empresa** — este repositório serve apenas para descrever os projetos, a arquitetura e as tecnologias.

---

## 1. Sistema de RH e Registo de Ponto — em produção

Aplicação usada todos os dias na fábrica, desenvolvida por mim de raiz.

**Tablet à entrada da fábrica**
- Picagem de ponto com número de empregado e código de 6 dígitos (entrada e, opcionalmente, saída).
- Atrasos obrigam a justificar (ou a pedir para falar com o RH).
- Pedidos de férias, justificação de faltas e pedidos para sair mais cedo.
- Calendário pessoal (horas, faltas, férias) e avisos do RH antes do login.
- Funciona **sem ligação à rede**: as picagens ficam guardadas e são sincronizadas depois.

**Área do RH (navegador)**
- Quadro do turno a decorrer: presentes, atrasados e em falta.
- Aprovação de férias, atrasos, faltas, horas extra e saídas antecipadas.
- Gestão de empregados, turnos rotativos e tablets.
- Horas do período de salários (26 a 25) com exportação para Excel.
- Mensagens e notificações para os empregados.

**Arquitetura**

```
Tablet (React Native / Expo)  ─┐
                               ├──►  API REST (Java 21 + Spring Boot) ──► PostgreSQL
Área do RH (React + TS + Vite) ┘        Spring Security · JPA · Flyway
```

- Back-end: Java 21, Spring Boot, Spring Security, Spring Data JPA, Flyway, Bean Validation
- Base de dados: PostgreSQL (Docker), esquema gerido por migrações Flyway
- Front-end: React + TypeScript + Vite; app do tablet em React Native (Expo) com modo offline
- Publicação: Docker, Caddy

---

## 2. Folhas de Produção Digitais — em desenvolvimento

Substituir as folhas de papel das máquinas de injeção por uma solução digital.

- **App do tablet** (React Native + Expo): a produção preenche as folhas de cada máquina, por turno.
- **Área de administração** (React + Vite): envio das folhas e quadro de acompanhamento.
- **API** em Java 21 + Spring Boot com PostgreSQL.

---

josejoao342@gmail.com · [Portfólio](https://jose-lameiras.github.io) · [LinkedIn](https://www.linkedin.com/in/jjlameiras)
