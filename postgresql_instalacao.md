**Instalação do PostgreSQL no Fedora 42**

https://www.postgresql.org/download/linux/redhat/

- Instalação dos pacotes e inicialização do serviço
```
sudo dnf install -y https://download.postgresql.org/pub/repos/yum/reporpms/F-42-x86_64/pgdg-fedora-repo-latest.noarch.rpm
sudo dnf install -y postgresql17-server
sudo /usr/pgsql-17/bin/postgresql-17-setup initdb
sudo systemctl enable postgresql-17
sudo systemctl start postgresql-17
```

- Edição do arquivo pg_hba.conf para liberar a permissão de acesso ao usuário "postgres"
```linux
vi /var/lib/pgsql/17/data/pg_hba.conf
```

- Alterar a configuração de autenticação local de **peer** para **trust**: \n
  Alterar de **peer**:
<img width="1485" height="452" alt="image" src="https://github.com/user-attachments/assets/1b25c316-0b95-4abb-818c-efc050271df8" />

para **trust**:
<img width="1530" height="478" alt="image" src="https://github.com/user-attachments/assets/7fc15832-dbde-46a3-ae15-b8776e04b4cb" />

Reiniciar o serviço do PostgreSQL
```
 sudo systemctl restart postgresql-17
```

Acessar o banco 
```
psql -U postgres
```
