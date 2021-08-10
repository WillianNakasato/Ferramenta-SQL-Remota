# Ferramenta-SQL-Remota
Fazendo a atividade do projeto "Ferramenta SQL Remota"
#!/usr/bin/python

import MySQLdb
import prettytable
from prettytable import from_db_cursor

host = input('Nome do host ')
user = input('Usuário ')
passwd = input('Senha ')
database = input('nome da base de dados ')
db = MySQLdb.connect(host, # seu host, usualmente o localhost
                     user, # seu usuário
                      passwd, # sua senha
                      database) # nome da base de dados)
                      
cur = db.cursor() 
col = input('Nome da coluna')
table = input('Nome da tabela')
#columns = map(col, col.split())
cur.execute("SELECT "+col+" FROM "+database+ "."+table+"")
pt = from_db_cursor(cur)
print pt
cur.close()
