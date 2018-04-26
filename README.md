"""
<br>Created on 26/03/2018
<br>@author: blackwolf
<br>@email : iory1987@gmail.com
<br>@name  : David Ferreira Gonçalves
<br>
"""

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.
    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.
    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>
    
    Copyleft 2015
    
 Stack do sistema de monitoramento zabbix utilizando elastic para armazenar dados das tabelas de history.<br>
 Para usar a stack é necessario ter o docker instalado, verção CE 17.x ou superior. [download docker](https://docs.docker.com/install/)<br>
 Precisamos também do docker compose, versão 18.0.x ou superior. [download docker-compose](https://docs.docker.com/compose/install/)<br>
 
 
 Para construção utilizamos quase todas as imagens oficiiais da zabbix sis, mysql e elastisearch.<br>
 A stack é composta de 4 serviços:
   - ElasticSearch: Utilizando a imagem oficial, subimos uma instancia para fazer o armazenamento dos logs que toma muito espaço no banco do zabbix.
   - MySQL: Sistema principal de armazenamento da stack. Como o zabbix foi desenvolvido, a principio com o mysql, o mesmo apresenta melhor permormace, vistão não estamos levando em conta nehum tunning feita por DBAs ou ADs.
   - ZabbixServer: Core do zabbix, sendo utilizado sem balanceamento de carga ou HA mas pode facilmente ser configurado usando pacemaker ou sistema parecidos.
   - Web Interface: Parte grafica do zabbix (vulgo GUI). Para essa parte da stack tive que modificar um pouco a imagem oficial pois a mesma não tinha opção de configurar o elk direto no zabbix.conf.php.
 
 Para rodar essa stack execute o seguinte comando: <code>sudo docker-compose up -d </code><br>
 Após a execução do comando espere o docker fazer o download das imagens.<br>
 Para verificar se está tudo certo é só rodar seguinte comando: <code>sudo docker-commpose ps</code><br>
 Todas as imagens utilizadas podem ser contradas no [docker hub](https://hub.docker.com/)<br>
 Utilize, compartilhe e melhore esse projeto, seja livre!
 
