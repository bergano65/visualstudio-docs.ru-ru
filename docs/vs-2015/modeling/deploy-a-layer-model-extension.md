---
title: Развертывание расширения модели слоев | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c11c952223854ff1b4b963e24615e7abe831496
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669865"
---
# <a name="deploy-a-layer-model-extension"></a>Развертывание расширения модели слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Другие пользователи Visual Studio могут устанавливать расширения моделирования слоев, созданные вами с помощью Visual Studio.

## <a name="installing-your-extension"></a>Установка расширения
 Расширение скомпилировано в VSIX-файл, который можно устанавливать на других компьютерах. Кроме того, расширение можно установить на компьютере разработки, чтобы сделать его доступным в главном экземпляре Visual Studio.

#### <a name="to-install-the-extension"></a>Установка расширения

1. В проекте, содержащем файл **source. VSIX. manifest**, откройте **bin \\ \\ *** в проводнике.

2. Скопируйте ** \* VSIX** файл на компьютер, на котором необходимо установить расширение.

3. На конечном компьютере дважды щелкните VSIX-файл в проводнике.

    Откроется установщик VSIX.

#### <a name="to-uninstall-the-extension"></a>Удаление расширения

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления**.

2. Щелкните имя расширения и нажмите кнопку **Удалить**.

## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Установка расширения на сервере Team Foundation Build
 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] на серверах обычно не установлен Visual Studio, поэтому нельзя установить VSIX, дважды щелкнув его. Установка [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] включает несколько компонентов для запуска расширения VSIX, но установка расширения выполняется вручную.

#### <a name="to-install-your-layer-extension-on-a-esprbuild-server"></a>Установка расширения слоев на сервере [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]

1. Скопируйте **VSIX** файлы с компьютера разработчика на [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] компьютер.

     Поместите VSIX-файл в одно из указанных ниже мест.

    - Установка для всех пользователей и служб:

         %ProgramFiles%\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft

    - Установка только для сетевой службы, в которой выполняется [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]:

         %Виндир%\сервицепрофилес\нетворксервице\аппдата\локал\микрософт\висуалстудио \\ [версия] \Extensions\Microsoft

    - Если сервер [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] настроен на выполнение в интерактивном режиме от имени определенного пользователя, установить расширение можно только для этого пользователя:

         %Локалаппдата%\микрософт\висуалстудио \\ [версия] \екстенсионс\микрософт

        > [!NOTE]
        > % LocalAppData% обычно *DriveName**: Users*аппдаталокал.

2. Разверните каждый VSIX-файл в папке в том же местоположении.

    1. Измените расширение имени файла с **VSIX** на **ZIP**.

    2. Извлеките содержимое ZIP-файла в папку.

    3. Удалите ZIP-файл.

3. Перезапустите [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].
