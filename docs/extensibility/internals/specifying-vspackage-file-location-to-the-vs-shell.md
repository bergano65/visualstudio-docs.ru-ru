---
title: Указание расположения файла VSPackage в оболочку VS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a4270fbd723e6c5aa6f16066066e0ca4ac74e5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Указание расположения файла VSPackage в оболочку VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо иметь возможность найти сборку библиотеки DLL для загрузки пакета VSPackage. Его можно найти различными способами, как описано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|Используйте раздел реестра CodeBase.|Ключ CodeBase может использоваться для направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки сборки VSPackage из любого полное имя пути. Значение ключа должно быть путь к библиотеке DLL. Это лучший способ иметь [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузить сборку пакета. Такой подход иногда называют «база кода и закрытого каталога метод.» Во время регистрации значение codebase передаются классов атрибутов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа.|  
|Поместите DLL в **PrivateAssemblies** каталога.|Поместите сборку в **PrivateAssemblies** подкаталог [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каталога. Сборки расположены в **PrivateAssemblies** обнаруживаются автоматически, но не отображаются в **Добавление ссылок** диалоговое окно. Разница между **PrivateAssemblies** и **PublicAssemblies** является то, что сборки в **PublicAssemblies** перечислены в **Добавление ссылок**  диалоговое окно. Если вы решили не использовать метод «каталог установки базы кода и закрытого», то следует установить в **PrivateAssemblies** каталога.|  
|Используйте сборки со строгим именем и раздел реестра сборки.|Ключ сборки можно использовать для явного перенаправления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки со строгим именем сборки VSPackage. Значение ключа должно быть строгое имя сборки.|  
|Поместите DLL в **PublicAssemblies** каталога.|Наконец, сборку можно также поместить в **PublicAssemblies** подкаталог. Сборки расположены в **PublicAssemblies** обнаруживаются автоматически, а также будут отображаться в **Добавление ссылок** диалоговое окно в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Сборки VSPackage должен быть помещен только в **PublicAssemblies** каталог, если они содержат управляемых компонентов, которые предназначены для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствуют этому критерию.|  
  
> [!NOTE]
>  Использование сборок со строгими именами, с подписью для всех зависимых сборок. Эти сборки должны быть установлены в собственный каталог или глобальный кэш сборок (GAC). Это обеспечивает защиту от конфликтует со сборками, имеющими же базовое имя файла, известные как weak имя привязки.