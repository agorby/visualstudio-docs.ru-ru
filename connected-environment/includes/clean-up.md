## <a name="clean-up"></a>Очистка
Чтобы полностью удалить среду подключения в Azure, в том числе все запущенные службы, используйте команду `vsce env rm`. Не забывайте, что это действие необратимо.

В следующем примере указаны подключенные среды в вашей действующей подписке Azure, а затем удаляется среда с именем myenv в группе ресурсов myenv-rg.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```
