---
title: 'Практическое: выполнение рабочего процесса с учетной записью пользователя | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08ac00384110cc73175286365fef6ee4b67a0170
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560215"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Практическое руководство. Выполнение рабочего процесса с учетной записью пользователя
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: запустить рабочий процесс в учетной записи пользователя](https://docs.microsoft.com/visualstudio/debugger/how-to-run-the-worker-process-under-a-user-account).  
  
Для настройки компьютера, чтобы можно было выполнить рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] (aspnet_wp.exe или w3wp.exe) с учетной записью пользователя, выполните следующие действия.  
  
## <a name="procedure"></a>Процедура  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Выполнение aspnet_wp.exe с учетной записью пользователя  
  
1.  Откройте файл machine.config в папке CONFIG данного компьютера, согласно пути, указанному при установке среды выполнения.  
  
2.  Найти &lt;processModel&gt; раздел и измените атрибуты пользователя и пароль для имени и пароля учетной записи пользователя, необходимо выполнить aspnet_wp.exe.  
  
3.  Сохраните файл machine.config.  
  
4.  По умолчанию в [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)] установлены службы IIS 6.0. Соответствующий рабочий процесс — w3wp.exe. Чтобы выполнить в режиме IIS 6.0 с aspnet_wp.exe в качестве рабочего процесса, необходимо выполнить следующие действия:  
  
    1.  Нажмите кнопку **Пуск**, щелкните пункт **Администрирование** , затем выберите пункт **Службы IIS**.  
  
    2.  В диалоговом окне **Службы IIS** щелкните правой кнопкой мыши папку **Веб-узлы** и выберите пункт **Свойства**.  
  
    3.  В диалоговом окне **Свойства веб-узлов** выберите **Службы**.  
  
    4.  Выберите команду **Запускать веб-службу в режиме изоляции IIS6.0**.  
  
    5.  Закройте диалоговые окна **Свойства** и **Диспетчер служб Интернета**.  
  
5.  Откройте командную строку Windows и перезапустите сервер с помощью команды:  
  
    ```  
    iisreset  
    ```  
    Или...  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Найдите папку Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files, которая находится по тому же пути, что и папка CONFIG. Щелкните правой кнопкой мыши временный [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] файлы, папки и выберите **свойства** в контекстном меню.  
  
7.  В диалоговом окне **Свойства: Temporary ASP.NET Files** перейдите на вкладку **Безопасность** .  
  
8.  Нажмите кнопку **Дополнительно**.  
  
9. В диалоговом окне **Дополнительные параметры безопасности для временных файлов ASP.Net** , нажмите кнопку **Добавить**.  
  
    Появится диалоговое окно **Выбор: пользователи, компьютеры или группы** .  
  
10. Введите имя пользователя в поле **Введите имена выбираемых объектов** , затем нажмите кнопку **OK**. Имя пользователя должно быть в формате ИмяДомена\ИмяПользователя.  
  
11. В диалоговом окне **Элемент разрешения для Temporary ASP.NET Files** предоставьте пользователю полный доступ с помощью пункта **Полный доступ**, затем нажмите кнопку **OK** , чтобы закрыть диалоговое окно **Запись для Temporary ASP.NET Files** .  
  
12. Появится диалоговое окно **Безопасность** с запросом, действительно ли необходимо изменить разрешения для системной папки. Нажмите кнопку **Да**.  
  
13. Нажмите кнопку **OK** , чтобы закрыть диалоговое окно **Свойства Temporary ASP.NET Files** .  
  
## <a name="see-also"></a>См. также  
[Отладка ASP.NET: системные требования](../debugger/aspnet-debugging-system-requirements.md)  
  




