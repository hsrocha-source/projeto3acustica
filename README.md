# Análise e Comparação de Algoritmos de Compressão de Áudio

Este projeto implementa e compara diferentes técnicas de codificação e compressão de áudio. O código realiza a análise de sinais de voz e sinais sintéticos (senóide e ruído branco) utilizando três abordagens principais: quantização uniforme (Baseline), quantização perceptual baseada na escala Bark e o codificador MP3 LAME.

# 1. Funcionalidades

## 1.1 Carregamento e Pré-processamento
Leitura de arquivos de áudio, normalização e conversão para mono.

## 1.2 Transformada
Aplicação da Transformada Discreta de Cosseno (DCT-IV) com janelamento Hann.

## 1.3 Quantização Baseline
Implementação de um quantizador uniforme escalar.

## 1.4 Quantização Perceptual
Implementação de um modelo psicoacústico simplificado utilizando bandas críticas da escala Bark para alocação dinâmica de bits baseada na energia das bandas.

## 1.5 Benchmarking com LAME
Utilização da biblioteca lameenc para gerar arquivos MP3 reais para comparação.

## 1.6 Otimização de Bitrate
Algoritmo de busca binária para encontrar os parâmetros de quantização ideais (delta ou fator de qualidade) que atinjam bitrates alvo (64, 96, 128 kbps).

## 1.7 Avaliação de Qualidade
- SNR (Signal-to-Noise Ratio): relação sinal-ruído.
- PESQ (Perceptual Evaluation of Speech Quality): métrica padronizada para qualidade de voz (MOS-LQO).

## 1.8 Visualização
Geração de gráficos comparativos de desempenho e espectrogramas.

# 2. Pré-requisitos

O código foi desenvolvido originalmente para execução no Google Colab. Para execução local ou em outro ambiente, são necessárias as seguintes bibliotecas Python:

- numpy
- scipy
- soundfile
- librosa
- pesq
- matplotlib
- lameenc
- pandas

# 3. Instalação das Dependências

pip install numpy scipy soundfile librosa pesq matplotlib lameenc pandas

# 4. Configuração do Ambiente

## 4.1 Arquivo de Entrada
- O script espera encontrar um arquivo de áudio específico para os testes de voz.
- Ajustar a variável file_path_1 para o caminho local do arquivo .wav.
- Comentar linhas referente ao google.colab e drive.mount ao executar localmente.

## 4.2 Sinais Sintéticos
O código gera automaticamente test_sine.wav e test_noise.wav para testes com sinais determinísticos e estocásticos.

# 5. Como Executar

Executar o script Python:

python projeto3.py

O script imprimirá:
- Informações do sinal de entrada
- Progresso da otimização de parâmetros
- Tabelas de SNR e PESQ

Arquivos gerados:
- rec_perfeito.wav
- baseline_[bitrate]kbps.wav
- perceptual_[bitrate]kbps.wav
- lame_[bitrate]kbps_decoded.wav

# 6. Estrutura do Código

- hz2bark / bark2hz: conversões de escala de frequência
- criar_bandas_bark: definição das bandas críticas
- quantizacao_baseline: quantização uniforme
- quantizacao_perceptual: quantização perceptual por bandas
- encontrar_parametro_ideal: otimização de bitrate
- calcular_snr / pesq: métricas de qualidade

# 7. Notas

A métrica PESQ wideband requer áudio reamostrado a 16 kHz (Wideband) ou 8 kHz (Narrowband). O script realiza automaticamente o resampling para 16 kHz antes da avaliação.
