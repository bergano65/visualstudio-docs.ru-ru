---
title: "Указание расположения файла VSPackage к оболочке VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "управляемых пакетов VSPackages расположение файла"
  - "Пакеты VSPackage, управляемых расположение файла пакета"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Указание расположения файла VSPackage к оболочке VS
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо иметь возможность найти сборку DLL для загрузки VSPackage. Его можно найти различными способами, как описано в следующей таблице.  
  
|Метод|Описание|  
|-----------|--------------|  
|Используйте раздел реестра базы кода.|CodeBase ключ может использоваться для направления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки VSPackage сборки из любой полному пути файла. Значение ключа должно быть путь к библиотеке DLL. Это лучший способ имеют [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] загрузить сборку пакета. Этот прием иногда называют «CodeBase и закрытого каталога методика установки.» Во время регистрации значение базы кода передается классы атрибутов регистрации через экземпляр <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> типа.|  
|Поместите DLL в **PrivateAssemblies** каталога.|Поместите сборку в **PrivateAssemblies** подкаталог [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] каталога. Сборки расположены в **PrivateAssemblies** обнаруживаются автоматически, но не отображаются в **Add References** диалоговое окно. Разница между **PrivateAssemblies** и **PublicAssemblies** является то, что сборки в **PublicAssemblies** перечисляются в **Add References** диалоговое окно. Если вы решили не использовать метод «каталог установки базы кода и закрытого», то следует установить в **PrivateAssemblies** каталога.|  
|Используйте сборки со строгим именем и реестра сборки.|Ключ сборки можно использовать для явного перенаправления [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для загрузки со строгим именем сборки VSPackage. Значение ключа должно быть строгое имя сборки.|  
|Поместите DLL в **PublicAssemblies** каталога.|Наконец, сборку можно разместить в **PublicAssemblies** подкаталог. Сборки расположены в **PublicAssemblies** обнаруживаются автоматически, а также будет отображаться в **Add References** диалогового окна в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> VSPackage сборки должен быть помещен только в **PublicAssemblies** каталог, если они содержат управляемые компоненты, предназначенные для повторного использования другими разработчиками VSPackage. Большинство сборок не соответствуют этому критерию.|  
  
> [!NOTE]
>  Использование сборок со строгими именами, с подписью для все зависимые сборки. Эти сборки также должно быть установлено в собственный каталог или в глобальный кэш сборок \(GAC\). Это обеспечивает защиту от конфликтует со сборками, имеющими же базовое имя файла, известные как слабый имя привязки.