---
title: 'Практическое: выполнение рабочего процесса с учетной записью пользователя | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e0caba3cce487f8a706aee7e0944a75255d1df6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939120"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Практическое руководство. Выполнение рабочего процесса с учетной записью пользователя
Для настройки компьютера, чтобы можно было выполнить рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (aspnet_wp.exe или w3wp.exe) с учетной записью пользователя, выполните следующие действия.  

 > [!IMPORTANT]
 > Начиная с Windows Server 2008 R2, мы рекомендуем использовать [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) с удостоверением, для каждого пула приложений.
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Выполнение aspnet_wp.exe с учетной записью пользователя  
  
1. Откройте файл machine.config в папке CONFIG данного компьютера, согласно пути, указанному при установке среды выполнения.  
  
2. Найти &lt;processModel&gt; раздел и измените атрибуты пользователя и пароль для имени и пароля учетной записи пользователя, необходимо выполнить aspnet_wp.exe.  
  
3. Сохраните файл machine.config.  
  
4. По умолчанию в [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)]установлены службы IIS 6.0. Соответствующий рабочий процесс — w3wp.exe. Чтобы выполнить в режиме IIS 6.0 с aspnet_wp.exe в качестве рабочего процесса, необходимо выполнить следующие действия:  
  
   1.  Нажмите кнопку **Пуск**, щелкните пункт **Администрирование** , затем выберите пункт **Службы IIS**.  
  
   2.  В диалоговом окне **Службы IIS** щелкните правой кнопкой мыши папку **Веб-узлы** и выберите пункт **Свойства**.  
  
   3.  В диалоговом окне **Свойства веб-узлов** выберите **Службы**.  
  
   4.  Выберите команду **Запускать веб-службу в режиме изоляции IIS6.0**.  
  
   5.  Закройте диалоговые окна **Свойства** и **Диспетчер служб Интернета**.  
  
5. Откройте командную строку Windows и перезапустите сервер с помощью команды:  
  
   ```cmd
   iisreset  
   ```  
   Или...  
  
   ```cmd
   net stop iisadmin /y  
   net start w3svc  
   ```  
  
6. Найдите папку Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files, которая находится по тому же пути, что и папка CONFIG. Щелкните правой кнопкой мыши папку Temporary [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Files и выберите в контекстном меню пункт **Свойства** .  
  
7. В диалоговом окне **Свойства: Temporary ASP.NET Files** перейдите на вкладку **Безопасность** .  
  
8. Нажмите кнопку **Дополнительно**.  
  
9. В диалоговом окне **Дополнительные параметры безопасности для временных файлов ASP.Net** , нажмите кнопку **Добавить**.  
  
    Появится диалоговое окно **Выбор: пользователи, компьютеры или группы** .  
  
10. Введите имя пользователя в поле **Введите имена выбираемых объектов** , затем нажмите кнопку **OK**. Имя пользователя должно быть в формате ИмяДомена\ИмяПользователя.  
  
11. В диалоговом окне **Элемент разрешения для Temporary ASP.NET Files** предоставьте пользователю полный доступ с помощью пункта **Полный доступ**, затем нажмите кнопку **OK** , чтобы закрыть диалоговое окно **Запись для Temporary ASP.NET Files** .  
  
12. Появится диалоговое окно **Безопасность** с запросом, действительно ли необходимо изменить разрешения для системной папки. Нажмите кнопку **Да**.  
  
13. Нажмите кнопку **OK** , чтобы закрыть диалоговое окно **Свойства Temporary ASP.NET Files** .  
  
## <a name="see-also"></a>См. также  
[Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
[Отладка ASP.NET: системные требования](../debugger/aspnet-debugging-system-requirements.md)  
  
