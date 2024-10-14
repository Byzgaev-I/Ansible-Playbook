# Домашнее задание "`"Работа с Playbook`"   

---

### Задание 

1) Подготовьте свой inventory-файл prod.yml.
2) Допишите playbook: нужно сделать ещё один play, который устанавливает и настраивает vector. Конфигурация vector должна деплоиться через template файл jinja2. От вас не требуется использовать все возможности шаблонизатора, просто вставьте стандартный конфиг в template файл. Информация по шаблонам по ссылке. не забудьте сделать handler на перезапуск vector в случае изменения конфигурации!  
3) При создании tasks рекомендую использовать модули: get_url, template, unarchive, file.  
4) Tasks должны: скачать дистрибутив нужной версии, выполнить распаковку в выбранную директорию, установить vector.  
5) Запустите ansible-lint site.yml и исправьте ошибки, если они есть.  
6) Попробуйте запустить playbook на этом окружении с флагом --check.  
7) Запустите playbook на prod.yml окружении с флагом --diff. Убедитесь, что изменения на системе произведены.  
8) Повторно запустите playbook с флагом --diff и убедитесь, что playbook идемпотентен.  
9) Подготовьте README.md-файл по своему playbook. В нём должно быть описано: что делает playbook, какие у него есть параметры и теги. Пример качественной документации ansible playbook по ссылке. Так же приложите скриншоты выполнения заданий №5-8  
10) Готовый playbook выложите в свой репозиторий, поставьте тег 08-ansible-02-playbook на фиксирующий коммит, в ответ предоставьте ссылку на него.


### Выполнение задания

1) Подготовил свой inventory-файл prod.yml.
2) Дописал playbook
5) Запустил ansible-lint site.yml и исправил ошибки.

   ![image.jpg](https://github.com/Byzgaev-I/Ansible-Playbook/blob/main/Снимок%20экрана%202024-10-14%20в%2004.51.58.png)

6-8) Запустил 

 ```yml
ansible-playbook /home/byzgaev12new/ansible-project/site.yml -i /home/byzgaev12new/ansible-project/prod.yml --diff
```
 ![image.jpg](https://github.com/Byzgaev-I/Ansible-Playbook/blob/main/Снимок%20экрана%202024-10-13%20в%2023.49.58.png)

 ![image.jpg](https://github.com/Byzgaev-I/Ansible-Playbook/blob/main/Снимок%20экрана%202024-10-14%20в%2000.05.24.png)

 
```
 root@Debian-New12:/home/byzgaev12new/ansible-project# ansible-playbook /home/byzgaev12new/ansible-project/site.yml -i /home/byzgaev12new/ansible-project/prod.yml --diff

PLAY [Install Clickhouse and Vector] **************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Install necessary dependencies] *************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Install python3-venv] ***********************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Create a virtual environment] ***************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
changed: [clickhouse-01]

TASK [Install Paramiko in virtual environment] ****************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
changed: [clickhouse-01]

TASK [Get Clickhouse distrib] *********************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Create directory for Clickhouse extraction] *************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Verify Clickhouse directory exists] *********************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Extract Clickhouse package] *****************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Check if Clickhouse client is installed] ****************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Install Clickhouse client] ******************************************************************************************************************************************************************
skipping: [clickhouse-01]

TASK [Ensure Clickhouse service is running] *******************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Create database] ****************************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
changed: [clickhouse-01]

PLAY [Install and configure Vector] ***************************************************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Download Vector package] ********************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
changed: [clickhouse-01]

TASK [Install Vector using deb package] ***********************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
Selecting previously unselected package vector.
(Reading database ... 217739 files and directories currently installed.)
Preparing to unpack /tmp/vector.deb ...
Unpacking vector (0.41.1-1) ...
Setting up vector (0.41.1-1) ...
systemd-journal:x:999:
changed: [clickhouse-01]

TASK [Create Vector config directory] *************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
ok: [clickhouse-01]

TASK [Deploy Vector configuration] ****************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
--- before
+++ after: /root/.ansible/tmp/ansible-local-7447zuqo8jsd/tmpji7ormf4/vector.toml.j2
@@ -0,0 +1,7 @@
+[sources.in]
+type = "stdin"
+
+[sinks.out]
+inputs = ["in"]
+type = "console"
+encoding.codec = "json"

changed: [clickhouse-01]

RUNNING HANDLER [Restart Vector] ******************************************************************************************************************************************************************
[WARNING]: sftp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
[WARNING]: scp transfer mechanism failed on [10.0.2.15]. Use ANSIBLE_DEBUG=1 to see detailed information
changed: [clickhouse-01]

PLAY RECAP ****************************************************************************************************************************************************************************************
clickhouse-01              : ok=18   changed=7    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0   
```



 Наш playbook успешно завершил выполнение всех задач, связанных с установкой и конфигурацией ClickHouse и Vector, без ошибок. Это значит, что все необходимые действия по установке и настройке этих компонентов были выполнены корректно.


Подведя итоги видим:
- Установка и настройка ClickHouse:
- Все задачи, связанные с установкой ClickHouse и проверкой его состояния, выполнены успешно.
- База данных logs была успешно создана.
- Установка и настройка Vector:
- Vector был загружен и установлен с использованием deb-пакета.
- Конфигурация была развернута из шаблона vector.toml.j2.
- Сервис Vector был успешно перезапущен.
  
  
Задание 9

# Ansible Playbook для установки ClickHouse и Vector

Этот плейбук предназначен для автоматизации установки и настройки ClickHouse и Vector на целевом хосте.

## Возможности

- **Установка ClickHouse**: Устанавливает ClickHouse указанной версии, гарантирует запуск сервиса и создает базу данных с названием `logs`.
- **Установка Vector**: Устанавливает Vector с использованием deb-пакета, настраивает его с помощью шаблона Jinja2 и гарантирует запуск сервиса.

## Структура плейбука

Плейбук состоит из двух основных разделов:

1. **Установка ClickHouse**:
   - Устанавливает необходимые зависимости.
   - Загружает и устанавливает ClickHouse.
   - Обеспечивает запуск сервиса ClickHouse.
   - Создает базу данных с именем `logs`.

2. **Установка и настройка Vector**:
   - Загружает и устанавливает Vector с использованием deb-пакета.
   - Разворачивает конфигурацию из шаблона.
   - Обеспечивает запуск сервиса Vector.

## Параметры

- **clickhouse_version**: Версия ClickHouse для установки.
- **vector_version**: Версия Vector для установки (через deb-пакет).

## Теги

- **clickhouse**: Теги задач, связанных с установкой и настройкой ClickHouse.
- **vector**: Теги задач, связанных с установкой и настройкой Vector.

## Использование

Для запуска плейбука используйте следующую команду:

```bash
ansible-playbook site.yml -i prod.yml --diff
```

11) https://github.com/Byzgaev-I/Ansible-Playbook/tags
