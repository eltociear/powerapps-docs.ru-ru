Выполняется после основной операции системы и в рамках транзакции базы данных.<br /><br />Эта стадия используется для изменения свойств сообщения до его возврата вызывающей стороне.<br /><br />Старайтесь не применять изменения к сущности, включенной в сообщение, поскольку это приведет к новому событию обновления.