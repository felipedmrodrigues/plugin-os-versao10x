# 📦 Plugin OS Adaptado para GLPI 10.0.x

Este repositório contém a versão **adaptada** do plugin **Ordem de Serviço (OS)** para o **GLPI 10.0.18**, com melhorias realizadas por **Felipe Melo** para otimizar a geração de PDFs, exibir o último acompanhamento do chamado e ajustar a logo do layout.

---

## ✅ Alterações Principais

- Compatível com **GLPI 10.0.18**
- PDF alterado para exibir o **último acompanhamento** ou a Solução do chamado. Você escolhe de acordo com o aruquivo baixado.
- Inclusão de **logo personalizada** no PDF
- Organização do repositório com **duas versões** do `os_pdf.php` para fácil comparação

---

## 🛠️ Requisitos

- GLPI 10.0.x 
- PHP 7.4 até 8.1
- Servidor Apache ou Nginx com permissões de escrita habilitadas
- Permissão de escrita nas pastas do plugin (`www-data` no Ubuntu)

---

## 🚀 Instalação

1. Acesse a pasta de plugins do GLPI:

```bash
cd /var/www/html/glpi/plugins
```

2. Clone este repositório de acordo com o que deseja implementar na o.s. Acompanhamento ou Solução:

```bash
git clone https://github.com/seuusuario/plugin-os-adaptado.git os
```

3. Ajuste as permissões para evitar erros de geração de arquivos e upload (Renomei o arquivo para apenas "os":

```bash
mv os-master os
chown -R www-data:www-data /var/www/html/glpi/plugins/os
chmod -R 775 /var/www/html/glpi/plugins/os
```

4. Ative o plugin no GLPI:

> Acesse: **Configurar > Plugins > Ordem de Serviço > Ativar**

---

## ⚙️ Configuração Necessária

### 🔗 Corrigir URL base

1. Acesse o GLPI
2. Vá em: **Configurar > Geral > Configuração**
3. Altere o campo **"Endereço da aplicação"** para:

```plaintext
http://seu-dns-ou-ip
```

> ⚠️ **Evite usar `localhost`**, pois isso impede a correta geração dos PDFs no navegador pricipalmente se estiver utilizando docker.

---

## 🖼️ Personalização da Logo

A imagem foi redimensionada para o padrão ideal de **300x100 pixels**.  
Para substituir sua logo personalizada no PDF, basta colocar o arquivo neste caminho:

```plaintext
plugins/os/pics/logo_os.png
```

> A logo incluída neste repositório já está no tamanho correto: `logo_vertical_300x100.png`

---

## 🔍 Comparativo de Versões

O repositório inclui duas versões do arquivo `os_pdf.php` para referência:

| Arquivo                          | Descrição                                                               |
|----------------------------------|-------------------------------------------------------------------------|
| `os_pdf.php.solução/os_pdf.php` | Versão original: exibe o campo **Solução** do chamado (`glpi_tickets.solution`) |
| `os_pdf.php.acompanhamento/os_pdf.php` | Versão adaptada: exibe o **último acompanhamento** (`glpi_itilfollowups.content`) |

---

