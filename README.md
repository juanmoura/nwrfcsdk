# nwrfcsdk
https://github.com/SAP/node-rfc/blob/main/doc/installation.md


#
#

## 1 - Desativar o modo stealth do MAC
`````
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode off
`````

## 2 - Criar o diretório padrão da lib
`````
sudo mkdir -p /usr/local/sap/nwrfcsdk
`````

## 3 - Setar a variável de ambiente
`````
echo "SAPNWRFC_HOME=/usr/local/sap/nwrfcsdk" >> ~/.zshrc
source ~/.zshrc
`````

## 4 - Executar o paths_fix.sh
`````
./paths_fix.sh

-- Obs: ignore os erros abaixo caso apareção

error: /Library/Developer/CommandLineTools/usr/bin/install_name_tool: input file: startrfcexec.sh is not a Mach-O file
`````
## 5 - Copiar o conteúdo da lib para a pasta padrão
`````
sudo cp -r ./* /usr/local/sap/nwrfcsdk/
`````

## 6 - Caso ao executar o node-rfc ocorra erro dizendo que não encontrou a lib execute o comando abaixo
`````
install_name_tool -rpath /usr/local/sap/nwrfcsdk/lib /usr/local/sap/nwrfcsdk_new/lib  /path-to-project/node_modules/node-rfc/lib/binding/sapnwrfc.node 
install_name_tool -rpath /usr/local/sap/nwrfcsdk_new/lib /usr/local/sap/nwrfcsdk/lib  /path-to-project/node_modules/node-rfc/lib/binding/sapnwrfc.node 
`````