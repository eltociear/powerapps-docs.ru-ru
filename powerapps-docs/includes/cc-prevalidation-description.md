В начальной операции эта стадия будет выполняться перед основной операцией системы.<br /><br />Это предоставляет возможность включить логику для отмены операции до транзакции базы данных.<br /><br />Последующие операции, запущенные расширениями, зарегистрированными на других стадиях, также пройдут через эту стадию, но будут включены в транзакцию вызывающих расширений.<br /><br />Эта стадия выполняется перед выполнением всех проверок безопасности с целью проверить, что вызывающий или выполнивший вход в систему пользователь имеет нужные разрешения на выполнение требуемой операции.