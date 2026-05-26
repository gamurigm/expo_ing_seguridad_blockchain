# Glosario Técnico y Tecnológico: Blockchain Empresarial y Financiero

Este documento recopila de manera estructurada los principales acrónimos, tecnologías y protocolos abordados en el análisis técnico de blockchain, la tokenización de activos (RWAs) y la infraestructura financiera digital. Está diseñado como material de consulta rápida y profundización para la exposición.

---

## 1. Conceptos Fundamentales y Arquitecturas de Red

### DLT (Distributed Ledger Technology / Tecnología de Libro Mayor Distribuido)
*   **Definición:** Categoría general de bases de datos descentralizadas que se replican y sincronizan entre múltiples nodos (computadores) independientes. Toda blockchain es una DLT, pero no todas las DLT son blockchains (por ejemplo, Directed Acyclic Graphs o DAGs como IOTA).
*   **Uso:** Es el término formal utilizado por instituciones financieras e informes gubernamentales para referirse a la infraestructura descentralizada.

### EVM (Ethereum Virtual Machine / Máquina Virtual de Ethereum)
*   **Definición:** El entorno de ejecución de código binario (bytecode) que procesa las transacciones y despliega contratos inteligentes en la red de Ethereum y otras cadenas compatibles (como Polygon, Avalanche C-Chain, Quorum o Monax).
*   **Importancia:** Se ha convertido en el estándar de desarrollo de la industria. Si una cadena es "EVM-compatible", significa que puede ejecutar cualquier contrato de Ethereum sin cambiar el código de origen.

### JVM (Java Virtual Machine / Máquina Virtual de Java)
*   **Definición:** Entorno que permite ejecutar programas escritos en Java, Kotlin o Scala.
*   **Uso:** En **R3 Corda**, las interacciones se ejecutan sobre la JVM en lugar de una EVM tradicional, facilitando que programadores corporativos usen lenguajes convencionales.

### L1 / L2 (Capa 1 y Capa 2 / Layer 1 & Layer 2)
*   **Capa 1 (Layer 1):** La blockchain principal e independiente (como Ethereum o Bitcoin) que se encarga del consenso definitivo y la seguridad.
*   **Capa 2 (Layer 2):** Soluciones de escalabilidad externas (como Polygon o Arbitrum) que procesan transacciones fuera de la L1 para reducir tarifas de gas y aumentar el rendimiento (TPS), enviando posteriormente pruebas comprimidas de vuelta a la L1.

---

## 2. Protocolos y Algoritmos de Consenso

### PoW (Proof of Work / Prueba de Trabajo)
*   **Definición:** Consenso basado en la resolución de problemas criptográficos de alta dificultad mediante potencia computacional. Fue el primer consenso (Bitcoin).
*   **Limitación:** Inviable para entornos empresariales debido a su baja velocidad y alto consumo eléctrico.

### PoS (Proof of Stake / Prueba de Participación)
*   **Definición:** Los validadores aseguran la red bloqueando capital (tokens) como garantía. Si se detectan fraudes, el sistema les penaliza confiscando sus fondos (*slashing*).
*   **Uso:** Utilizado por Ethereum L1 desde 2022 (*The Merge*) y Polygon.

### PoH (Proof of History / Prueba de Historia)
*   **Definición:** Algoritmo de temporización criptográfico propuesto por **Solana** que crea un registro histórico e inmutable del momento en que ocurren las transacciones. 
*   **Ventaja:** Funciona como un reloj distribuido que ordena las transacciones cronológicamente antes del consenso, permitiendo el procesamiento masivo en paralelo (hasta 65,000 TPS).

### PoET (Proof of Elapsed Time / Prueba de Tiempo Transcurrido)
*   **Definición:** Consenso diseñado por Intel que asigna un temporizador aleatorio a cada nodo. El primer temporizador en llegar a cero autoriza al nodo a firmar el bloque.
*   **Tecnología:** Utiliza hardware de Intel (**SGX**) para garantizar que el tiempo asignado no sea manipulado.

### PBFT (Practical Byzantine Fault Tolerance / Tolerancia Práctica a Fallos Bizantinos)
*   **Definición:** Protocolo que resuelve el problema de los Generales Bizantinos asumiendo que hasta $f$ nodos pueden fallar o mentir en una red de $3f+1$ participantes (soporta un 33% de fallos).
*   **Uso:** Hyperledger Fabric y redes de consorcio cerradas. Su limitación es la sobrecarga de red ($O(N^2)$).

### FBA (Federated Byzantine Agreement / Acuerdo Bizantino Federado)
*   **Definición:** Modelo donde cada validador define sus "rebanadas de quórum" (subgrupos en los que confía). El consenso se alcanza sin necesidad de que todos los nodos conozcan al resto.
*   **Uso:** Implementado en **Stellar Consensus Protocol (SCP)** y **Ripple**.

---

## 3. Criptografía y Estándares de Datos

### ECDSA (Elliptic Curve Digital Signature Algorithm / Algoritmo de Firma Digital de Curva Elíptica)
*   **Definición:** Criptografía de clave pública-privada basada en las propiedades matemáticas de curvas elípticas. Es el estándar para firmar y validar transacciones en redes como Bitcoin y Ethereum.
*   **Uso en RWA:** Permite al emisor de la contabilidad *off-chain* firmar digitalmente autorizaciones de cobro que el contrato inteligente en la cadena (*on-chain*) valida instantáneamente.

### EIP-712 (Ethereum Improvement Proposal 712)
*   **Definición:** Protocolo estándar para la firma y visualización de datos estructurados con formato legible por humanos en las billeteras Web3.
*   **Aplicación:** Evita que el usuario firme textos encriptados ilegibles (hashes crípticos), permitiéndole revisar con precisión el reclamo de dividendos antes de autorizarlo con su clave privada.

### ZKP (Zero-Knowledge Proof / Pruebas de Conocimiento Cero)
*   **Definición:** Técnica criptográfica que permite a una parte (el probador) demostrar a otra (el verificador) que una declaración es verdadera sin revelar ninguna información más allá de la veracidad de la declaración.
*   **Uso en KYC:** Un usuario puede demostrar que es mayor de edad o que reside en un país permitido para operar sin revelar su fecha de nacimiento real o dirección física.

### TEE / Intel SGX (Trusted Execution Environment / Software Guard Extensions)
*   **Definición:** Enclaves seguros de hardware a nivel de procesador que aíslan el código y los datos de ejecución para evitar modificaciones externas, incluso por parte del administrador del sistema.
*   **Uso:** Implementación del reloj de seguridad en **PoET** e infraestructuras privadas de custodia.

---

## 4. Tokenización y Finanzas Descentralizadas (DeFi)

### RWA (Real World Assets / Activos del Mundo Real)
*   **Definición:** La representación digital en blockchain de activos físicos o financieros tradicionales (acciones, bonos de tesorería, bienes inmuebles, materias primas).
*   **Uso corporativo:** Fondos como BUIDL (BlackRock) tokenizan letras del tesoro norteamericano permitiendo liquidez inmediata en dólares digitales.

### ERC-20 / ERC-721 / ERC-3643
*   **ERC-20:** Estándar de tokens fungibles (intercambiables 1:1, como stablecoins y acciones fraccionadas).
*   **ERC-721:** Estándar de tokens no fungibles (NFTs, representativos de activos únicos como escrituras de tierras).
*   **ERC-3643:** Estándar de tokens de valores (security tokens) que incorpora controles de cumplimiento regulatorio y KYC directamente en el código de transferencia del token.

### AMM (Automated Market Maker / Creador de Mercado Automatizado)
*   **Definición:** Protocolos de intercambio descentralizado (como Uniswap) que eliminan el libro de órdenes tradicional de los bancos y usan pools de liquidez automatizados gobernados por ecuaciones matemáticas ($x \times y = k$).

### RTGS (Liquidación Bruta en Tiempo Real) y Redes Blockchain
*   **Definición:** Sistemas interbancarios que liquidan pagos inmediatamente.
*   **Vínculo Blockchain:** Las cadenas L1 públicas o los consorcios privados (como Quorum o Ripple) actúan nativamente como redes RTGS de alcance global descentralizado sin depender de un banco central, aunque enfrentan el desafío de requerir alta liquidez pre-depositada.

### DNS (Liquidación Neta Diferida) y Canales de Estado
*   **Vínculo Blockchain:** En lugar de sistemas DNS tradicionales (que acumulan alto riesgo crediticio intradía), la tecnología de *Canales de Estado* (como Lightning Network o canales privados en Hyperledger Fabric) permite compensaciones netas diferidas sin riesgo, ya que el capital queda garantizado criptográficamente en la cadena base.

### LSM (Ahorro de Liquidez) y Contratos Inteligentes
*   **Definición:** Mecanismos que cruzan colas de pagos pendientes para optimizar la liquidez.
*   **Vínculo Blockchain:** Se pueden programar como **Smart Contracts** autónomos que escanean el estado de la red (basándose en modelos estocásticos de redes de colas) para ejecutar automáticamente emparejamientos de pagos entre múltiples bancos de manera descentralizada e inmutable.

---

## 5. Regulación, Identidad y Modelos Bancarios

### MiCA (Markets in Crypto-Assets / Mercados de Criptoactivos)
*   **Definición:** Reglamento pionero de la Unión Europea que unifica la regulación de todos los proveedores de servicios criptográficos y emisores de tokens (incluidos los activos RWA), exigiendo reservas 1:1 verificables *on-chain*.

### Ley GENIUS (GENIUS Act - EE.UU.) e Implementación Técnica
*   **Definición:** Propuesta regulatoria estadounidense (de mediados de 2025) que otorga estatus legal pleno a las **Stablecoins** bancarias y privadas a nivel federal.
*   **Vínculo Blockchain:** Obliga a implementar dos controles a nivel de código (Smart Contracts): 1) **Proof of Reserves (PoR):** Oráculos que bloquean la emisión de tokens (`mint`) si no se detecta respaldo físico 1:1 en cuentas bancarias. 2) **Listas Negras (RBAC):** Funciones integradas (`blacklist`, `freeze`) que permiten a los emisores bloquear fondos ilícitos para cumplir con políticas Anti-Lavado de Dinero (AML) dentro de redes públicas.

### Identidad KYC Descentralizada
*   **Definición:** Marcos regulatorios (Know Your Customer) obligatorios para verificar la identidad real de los usuarios en entornos web3 o consorcios empresariales.
*   **Vínculo Blockchain:** Mediante la DLT combinada con Pruebas de Conocimiento Cero (ZKP), los bancos pueden validar el KYC de un cliente sin necesidad de enviarse mutuamente bases de datos privadas vulnerables.

### NPL (Non-Performing Loans / Préstamos en Mora)
*   **Vínculo Blockchain:** La falta de información compartida entre bancos eleva el riesgo crediticio (NPLs). Una DLT bancaria compartida de historial crediticio encriptado ayuda a auditar colaborativamente el perfil del cliente sin comprometer secretos comerciales, reduciendo sistemáticamente estas tasas.

---

## 6. Referencias Bibliográficas y Fuentes Académicas

### 1. Documento 1: Redes de Consorcio y Algoritmos de Consenso Empresariales
*   **Cita APA:** Ben Hamida, E., Brousmiche, K. L., Levard, H., & Thea, E. (2017). *Blockchain for Enterprise: Overview, Opportunities and Challenges*. SystemX; SQLI. HAL Id: hal-01591859.
*   **Cita IEEE:** E. Ben Hamida, K. L. Brousmiche, H. Levard, and E. Thea, "Blockchain for Enterprise: Overview, Opportunities and Challenges," SystemX, SQLI, France, Tech. Rep. HAL Id: hal-01591859, 2017.
*   **Enlace de Acceso:** [HAL Open Science (hal-01591859)](https://hal.science/hal-01591859v1)
*   **Conceptos en Glosario:** DLT, L1/L2, PoW, PoET, PBFT, TEE / Intel SGX.

### 2. Documento 2: Transformación Bancaria y Casos de Negocio
*   **Cita APA:** Guo, Y., & Liang, C. (2016). Blockchain application and outlook in the banking industry. *Financial Innovation*, *2*(1), 24.
*   **Cita IEEE:** Y. Guo and C. Liang, "Blockchain application and outlook in the banking industry," *Financial Innovation*, vol. 2, no. 1, p. 24, Dec. 2016.
*   **Enlace DOI:** [DOI: 10.1186/s40854-016-0034-9](https://doi.org/10.1186/s40854-016-0034-9)
*   **Conceptos en Glosario:** ZKP, FBA, KYC / AML, NPL.

### 3. Documento 3: Tokenización de Activos (RWA) y Redes de Pago Interbancario (RTGS)
*   **Cita APA:** Li, R. K. X. (2025). *A Blockchain Securities Tokenization Framework and a Stochastic Analysis of Interbank Payment Networks* (Master's thesis). University of Toronto, Toronto, Canadá.
*   **Cita IEEE:** R. K. X. Li, "A Blockchain Securities Tokenization Framework and a Stochastic Analysis of Interbank Payment Networks," Master's thesis, Dept. Appl. Sci., Univ. Toronto, Toronto, ON, 2025.
*   **Enlaces de Acceso:** [Preprint DOI (Research Square)](https://doi.org/10.21203/rs.3.rs-5759969/v1) | [University of Toronto TSpace (Tesis Completa)](https://hdl.handle.net/1807/139045)
*   **Conceptos en Glosario:** EVM, PoS, ECDSA, EIP-712, RWA, ERC-20 / ERC-721 / ERC-3643, AMM, RTGS, DNS, LSM.

### Bibliografía Complementaria (Fundamentos Tecnológicos y Regulatorios)

Esta sección incluye los documentos técnicos (*Whitepapers* y *Yellow Papers*) fundamentales y los marcos regulatorios directos que sustentan la tecnología explicada en el glosario.

*   **Ethereum y Contratos Inteligentes (EVM):**
    *   **Cita APA:** Wood, G. (2014). *Ethereum: A secure decentralised generalised transaction ledger*. Ethereum Project Yellow Paper, 151(2014), 1-32.
    *   **Cita IEEE:** G. Wood, "Ethereum: A secure decentralised generalised transaction ledger," *Ethereum Project Yellow Paper*, vol. 151, pp. 1-32, 2014.
*   **Hyperledger Fabric y Consensos Corporativos (PBFT):**
    *   **Cita APA:** Androulaki, E., Barger, A., Bortnikov, V., Cachin, C., Christidis, K., De Caro, A., ... & Yellick, J. (2018). Hyperledger fabric: a distributed operating system for permissioned blockchains. In *Proceedings of the thirteenth EuroSys conference* (pp. 1-15). [DOI: 10.1145/3190508.3190538](https://doi.org/10.1145/3190508.3190538)
    *   **Cita IEEE:** E. Androulaki et al., "Hyperledger fabric: a distributed operating system for permissioned blockchains," in *Proc. 13th EuroSys Conf.*, 2018, pp. 1-15.
*   **Avalanche y Consenso Snowball (Subnets):**
    *   **Cita APA:** Team Rocket, Yin, M., Sekniqi, K., van Renesse, R., & Sirer, E. G. (2019). Scalable and probabilistic leaderless BFT consensus through metastability. *arXiv preprint arXiv:1906.08936*.
    *   **Cita IEEE:** Team Rocket, M. Yin, K. Sekniqi, R. van Renesse, and E. G. Sirer, "Scalable and probabilistic leaderless BFT consensus through metastability," *arXiv preprint arXiv:1906.08936*, 2019.
*   **Solana y Proof of History (PoH):**
    *   **Cita APA:** Yakovenko, A. (2018). Solana: A new architecture for a high performance blockchain v0.8.13. *Whitepaper*.
    *   **Cita IEEE:** A. Yakovenko, "Solana: A new architecture for a high performance blockchain v0.8.13," Whitepaper, 2018.
*   **Marco Regulatorio Europeo (MiCA):**
    *   **Cita APA:** Parlamento Europeo y Consejo de la Unión Europea. (2023). *Reglamento (UE) 2023/1114 relativo a los mercados de criptoactivos (MiCA)*. Diario Oficial de la Unión Europea.
    *   **Cita IEEE:** European Parliament and Council of the European Union, "Regulation (EU) 2023/1114 on markets in crypto-assets (MiCA)," *Official Journal of the European Union*, 2023.
*   **Ingeniería de Stablecoins (Ley GENIUS y Proof of Reserves):**
    *   **Cita APA:** Klages-Mundt, A., Harz, D., Gudgeon, L., Liu, L., & Miers, I. (2020). Stablecoins 2.0: Economic foundations and risk-based models. In *Proceedings of the 2nd ACM Conference on Advances in Financial Technologies* (pp. 59-79). [DOI: 10.1145/3419614.3423261](https://doi.org/10.1145/3419614.3423261)
    *   **Cita IEEE:** A. Klages-Mundt, D. Harz, L. Gudgeon, L. Liu, and I. Miers, "Stablecoins 2.0: Economic foundations and risk-based models," in *Proc. 2nd ACM Conf. Adv. Financial Technol.*, 2020, pp. 59-79.
