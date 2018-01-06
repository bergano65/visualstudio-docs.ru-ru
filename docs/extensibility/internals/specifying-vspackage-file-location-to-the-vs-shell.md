---
title: "Указание расположения файла VSPackage в оболочку VS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35bd935683f8ace47536389ebc65f34311e9fcfd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Указание расположения файла VSPackage в оболочку VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]необходимо иметь возможность найти сборку библиотеки DLL для загрузки пакета VSPackage. Его можно найти различными способами, как описано в следующей таблице.  
  
|Метод|Описание:|  
|------------|-----------------|  
|Используйте раздел реестра CodeBase.|Ключ CodeBase может использоваться для направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки сборки VSPackage из любого полное имя пути. Значение ключа должно быть путь к библиотеке DLL. Это лучший способ иметь [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузить сборку пакета. Такой подход иногда называют «база кода и закрытого каталога метод.» Во время регистрации значение codebase передаются классов атрибутов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа.|  
|Поместите DLL в **PrivateAssemblies** каталога.|Поместите сборку в **PrivateAssemblies** подкаталог [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каталога. Сборки расположены в **PrivateAssemblies** обнаруживаются автоматически, но не отображаются в **Добавление ссылок** диалоговое окно. Разница между **PrivateAssemblies** и **PublicAssemblies** является то, что сборки в **PublicAssemblies** перечислены в **Добавление ссылок**  диалоговое окно. Если вы решили не использовать метод «каталог установки базы кода и закрытого», то следует установить в **PrivateAssemblies** каталога.|  
|Используйте сборки со строгим именем и раздел реестра сборки.|Ключ сборки можно использовать для явного перенаправления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки со строгим именем сборки VSPackage. Значение ключа должно быть строгое имя сборки.|  
|Поместите DLL в **PublicAssemblies** каталога.|Наконец, сборку можно также поместить в **PublicAssemblies** подкаталог. Сборки расположены в **PublicAssemblies** обнаруживаются автоматически, а также будут отображаться в **Добавление ссылок** диалоговое окно в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Сборки VSPackage должен быть помещен только в **PublicAssemblies** каталог, если они содержат управляемых компонентов, которые предназначены для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствуют этому критерию.|  
  
> [!NOTE]
>  Использование сборок со строгими именами, с подписью для всех зависимых сборок. Эти сборки должны быть установлены в собственный каталог или глобальный кэш сборок (GAC). Это обеспечивает защиту от конфликтует со сборками, имеющими же базовое имя файла, известные как weak имя привязки.