---
title: Использование Emulator Express для запуска и отладки облачной службы Azure на локальном компьютере | Документация Майкрософт
description: Использование Emulator Express для запуска и отладки облачной службы на локальном компьютере
author: mikejo5000
manager: douge
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 28dd59e3d691df0199afffe93d68d60668c6afe4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002344"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Использование Emulator Express для запуска и отладки облачной службы Azure на локальном компьютере
При использовании Emulator Express, можно протестировать и отладки облачной службы, не запуская Visual Studio с правами администратора. Можно задать параметры проекта, чтобы использовать Emulator Express или полный эмулятор, в зависимости от требований облачной службы. Дополнительные сведения о полном эмуляторе см. в разделе [запуск приложения Azure в эмуляторе вычислений](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Использование Emulator Express в Visual Studio
При создании проекта Azure в Azure SDK 2.3 или более поздней версии Emulator Express используется автоматически. Для существующих проектов, которые были созданы с помощью более ранней версии пакета SDK для Azure следуйте инструкциям ниже, выбрать Emulator Express:

1. Создайте или откройте проект облачной службы Azure в Visual Studio.

1. В **обозревателе решений**, щелкните правой кнопкой мыши проект и в контекстном меню выберите **свойства**.

1. На странице свойств проекта, выберите **Web** вкладки.

    ![Свойства для проекта облачной службы](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. В разделе **локальный сервер Development Server**выберите **использовать IIS Express**.

1. В разделе **эмулятор**выберите **использовать Emulator Express**.
   
1. Чтобы запустить Emulator Express, выполните следующую команду в командной строке: 

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Ограничения Emulator Express
Ниже перечислены известные ограничения Emulator Express: 

- Emulator Express несовместим с веб-сервера IIS.
- Облачная служба может содержать несколько ролей, но каждая роль ограничена одним экземпляром.
- Не удается получить доступ к номерам портов ниже 1000. Если вы используете поставщик проверки подлинности обычно использует порт с номером меньше 1000, может потребоваться изменить это значение к номеру порта выше 1000.
- Все ограничения, которые применяются к эмулятора вычислений Azure также применяются к Emulator Express. Например не может иметь более чем 50 экземпляров роли в развертывании. Дополнительные сведения об эмуляторе вычислений Azure см. в разделе [запуск приложения Azure в эмуляторе вычислений](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Следующие шаги
[Отладка облачных служб Azure](https://msdn.microsoft.com/library/azure/ee405479.aspx)
