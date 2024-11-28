Introdução ao Repositório: Instalação do Sistema Operacional no Raspberry Pi

Bem-vindo! Este repositório é voltado para auxiliar no uso e desenvolvimento com o Raspberry Pi. Para começar, vamos abordar como instalar o sistema operacional no seu dispositivo de maneira simples, mesmo que você não tenha experiência prévia.

Passo 1: Baixar e instalar o Raspberry Pi Imager
Acesse o site oficial da Raspberry Pi https://www.raspberrypi.com/software/
Faça o download do Raspberry Pi Imager para o seu sistema operacional (Windows, Mac ou Ubuntu).
Após o download, execute o arquivo de instalação:
Clique em Install.
Quando finalizar, clique em Finish para concluir. Se quiser abrir o Imager imediatamente, mantenha marcada a opção Run Raspberry Pi Imager.

Passo 2: Preparar a instalação do sistema operacional
Abra o Raspberry Pi Imager (procure por "Imager" na barra de pesquisa do Windows, caso necessário).
No Imager:
Escolha o modelo do seu Raspberry Pi.
Selecione o sistema operacional desejado (32 ou 64 bits, conforme a compatibilidade do seu dispositivo).
Escolha o local onde a imagem será gravada (cartão de memória, pen drive, etc.).
Clique em Write e aguarde a gravação ser concluída.

Passo 3: Configurar o Raspberry Pi
Insira o cartão de memória ou pen drive no Raspberry Pi e ligue-o.

Importante: Certifique-se de que a fonte de alimentação do Raspberry Pi fornece 5V e 3A.
Após ligar, siga as instruções na tela para a configuração inicial:

País, idioma e fuso horário: Escolha conforme sua localização. (Opcional: marque se deseja usar o teclado americano ou idioma em inglês).
Senha: Por padrão, a senha é raspberry, mas você pode alterá-la para maior segurança.
Ajuste de tela: Caso veja uma borda preta na tela, marque a caixa correspondente. Se estiver usando uma TV 4K, geralmente é melhor deixar essa opção desmarcada.
Conexão à Internet: Conecte-se via cabo ou Wi-Fi. Se não encontrar sua rede, isso pode ser configurado mais tarde.
Atualização de software: O sistema verificará por atualizações e as aplicará automaticamente.
Reinicie o Raspberry Pi quando solicitado.

Passo 4: Finalizar a configuração e atualizar o sistema
Após reiniciar, abra o terminal (ícone preto com um ">" no canto superior).
No terminal, execute os seguintes comandos para atualizar os pacotes do sistema:
sudo apt update
sudo apt upgrade
Confirme as ações digitando S ou Y (dependendo do idioma do sistema).

O que você já tem instalado?
Seu Raspberry Pi está pronto para uso! Ele vem com ferramentas como Geany e Thonny, que podem ser acessadas pelo menu (ícone de framboesa vermelha) em Desenvolvimento. Para ajustes adicionais, acesse Preferências > Raspberry Pi Configuration.

Com isso, seu sistema está configurado e pronto para projetos incríveis!!
