---
title: "Развертывание расширения модели слоев | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: "27"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 0569b5cced2100e1ed3b746464b001d929a209be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="deploy-a-layer-model-extension"></a>Развертывание расширения модели слоев
Другие пользователи Visual Studio могут устанавливать расширения моделирования слоев, созданные вами с помощью Visual Studio.  
  
## <a name="installing-your-extension"></a>Установка расширения  
 Расширение скомпилировано в VSIX-файл, который можно устанавливать на других компьютерах. Кроме того, расширение можно установить на компьютере разработки, чтобы сделать его доступным в главном экземпляре Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Установка расширения  
  
1.  В проекте, который содержит **source.vsix.manifest**откройте **bin\\ \***  в проводнике.  
  
2.  Копировать  **\*.vsix** файл на компьютер, на котором требуется установить расширение.  
  
3.  На конечном компьютере дважды щелкните VSIX-файл в проводнике.  
  
     Откроется установщик VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Удаление расширения  
  
1.  В Visual Studio на **средства** меню, нажмите кнопку **расширения и обновления**.  
  
2.  Выберите имя расширения и нажмите кнопку **удаления**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Установка расширения на сервере Team Foundation Build  
 Как правило, на серверах [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] не установлена среда Visual Studio, поэтому установить VSIX двойным щелчком мыши невозможно. Установка [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] включает несколько компонентов для запуска расширения VSIX, но установка расширения выполняется вручную.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Установка расширения слоев на сервере [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]  
  
1.  Копировать **.vsix** файлы с компьютера разработчика для [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] компьютера.  
  
     Поместите VSIX-файл в одно из указанных ниже мест.  
  
    -   Установка для всех пользователей и служб:  
  
         %ProgramFiles%\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft  
  
    -   Установка только для сетевой службы, в которой выполняется [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [версия]  
  
    -   Если сервер [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] настроен на выполнение в интерактивном режиме от имени определенного пользователя, установить расширение можно только для этого пользователя:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [версия]  
  
        > [!NOTE]
        >  % LocalAppData % — *DriveName*: пользователи*UserName*AppDataLocal.  
  
2.  Разверните каждый VSIX-файл в папке в том же местоположении.  
  
    1.  Измените расширение имени файла с **.vsix** для **.zip**.  
  
    2.  Извлеките содержимое ZIP-файла в папку.  
  
    3.  Удалите ZIP-файл.  
  
3.  Перезапустите [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
