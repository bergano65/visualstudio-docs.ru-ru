---
title: Запуск и отладка облачной службы Azure на локальном компьютере с помощью Emulator Express
description: Использование Emulator Express для запуска и отладки облачной службы на локальном компьютере
author: mikejo5000
manager: jillfra
ms.assetid: 73108f98-a552-4817-b7a1-551367b71906
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/06/2017
ms.author: mikejo
ms.openlocfilehash: 86ec00f5fdd80f4c42fdaf1d7c5c44e6008983de
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260677"
---
# <a name="using-emulator-express-to-run-and-debug-an-azure-cloud-service-on-a-local-machine"></a>Использование Emulator Express для запуска и отладки облачной службы Azure на локальном компьютере
Emulator Express позволяет протестировать и отладить облачную службу, не запуская Visual Studio от имени администратора. В зависимости от требований облачной службы параметры проекта можно задать таким образом, чтобы использовался либо Emulator Express, либо полный эмулятор. Дополнительные сведения о полном эмуляторе см. в статье [Запуск приложения Azure в эмуляторе вычислений](/azure/storage/common/storage-use-emulator).

## <a name="using-emulator-express-in-visual-studio"></a>Использование Emulator Express в Visual Studio
При создании проекта Azure в пакете Azure SDK 2.3 или более поздней версии Emulator Express используется автоматически. Для существующих проектов, созданных с использованием более ранней версии пакета Azure SDK, выбрать Emulator Express позволяет выполнение описанных ниже действий.

1. Создайте или откройте проект облачной службы Azure в среде Visual Studio.

1. В **обозревателе решений** щелкните проект правой кнопкой мыши и в контекстном меню выберите пункт **Свойства**.

1. На странице свойств проекта выберите вкладку **Веб**.

    ![Свойства проекта облачной службы Azure](./media/vs-azure-tools-emulator-express-debug-run/web-properties.png)

1. В разделе **Локальный сервер Development Server** выберите **Использовать IIS Express**.

1. В разделе **Эмулятор** выберите **Использовать Emulator Express**.

1. Чтобы запустить Emulator Express, выполните следующую команду в командной строке:

    ```
    csrun.exe /useemulatorexpress
    ```

## <a name="emulator-express-limitations"></a>Ограничения Emulator Express
Ниже перечислены известные ограничения Emulator Express.

- Emulator Express несовместим с веб-сервером IIS.
- Облачная служба может содержать несколько ролей, однако каждая роль ограничивается одним экземпляром.
- Невозможен доступ к портам с номерами меньше 1000. Это значит, что если ваш поставщик проверки подлинности обычно использует порт с номером меньше 1000, то вам придется изменить его на порт с номером больше 1000.
- Все ограничения, связанные с эмулятором вычислений Azure, применяются также к Emulator Express. Например, число экземпляров роли в развернутой службе не может быть больше 50. Дополнительные сведения об эмуляторе вычислений Azure см. в статье [Запуск приложения Azure в эмуляторе вычислений](http://go.microsoft.com/fwlink/p/?LinkId=623050).

## <a name="next-steps"></a>Следующие шаги
[Отладка облачных служб Azure](vs-azure-tools-debugging-cloud-services-overview.md)
