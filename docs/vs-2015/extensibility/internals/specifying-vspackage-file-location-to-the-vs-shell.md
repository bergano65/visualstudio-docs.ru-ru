---
title: Выбор расположения файла VSPackage к оболочке VS | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9e81ce857f6a37a709d46c3ee0567cb3cb203cb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281337"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Выбор расположения файла VSPackage к оболочке Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] должен иметь возможность найти сборку библиотеки DLL для загрузки VSPackage. Его можно найти различными способами, как описано в следующей таблице.  
  
|Метод|Описание|  
|------------|-----------------|  
|Используйте раздел реестра CodeBase.|Ключ базы кода может использоваться для направления [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для загрузки VSPackage сборки из любого полное имя пути. Значение ключа должно содержать путь файла к библиотеке DLL. Это лучший способ иметь [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] загрузить сборку пакета. Этот способ иногда называют «CodeBase и закрытого directory методика установки.» Во время регистрации значение базы кода, передается в качестве атрибута классов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа.|  
|Поместите библиотеки DLL в **PrivateAssemblies** каталога.|Поместите сборку в **PrivateAssemblies** подкаталог [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] каталога. Сборки расположены в **PrivateAssemblies** определяются автоматически, но не отображаются в **Add References** диалоговое окно. Разница между **PrivateAssemblies** и **PublicAssemblies** является то, что сборки в **PublicAssemblies** перечислены в **Добавление ссылок**  диалоговое окно. Если вы решили не использовать метод «каталог установки базы кода/private», то следует установить в **PrivateAssemblies** каталога.|  
|Используйте является сборкой со строгим именем и ключ реестра сборки.|Ключ сборки можно использовать для явного перенаправления [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для загрузки со строгим именем сборки VSPackage. Значение ключа должно быть строгое имя сборки.|  
|Поместите библиотеки DLL в **PublicAssemblies** каталога.|Наконец, сборку можно также поместить **PublicAssemblies** подкаталог. Сборки расположены в **PublicAssemblies** автоматически обнаруживаются, а также будут отображаться в **Add References** диалогового окна в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].<br /><br /> Сборки VSPackage должен быть помещен только в **PublicAssemblies** каталог, если они содержат управляемых компонентов, которые предназначены для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствуют этому критерию.|  
  
> [!NOTE]
>  Использование сборок со строгим именем, с подписью для все зависимые сборки. Эти сборки также должны быть установлены на собственного каталога или глобальном кэше сборок (GAC). Это обеспечивает защиту от конфликтует со сборками, имеющими то же имя базового файла, известный как weak имя привязки.

