---
title: Выбор каталога установки для VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697247"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Выбор каталога установки для VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет VSPackage и его вспомогательные файлы должны находиться в файловой системе пользователя. Расположение зависит от того, является ли VSPackage управляемым или неуправляемым, вашей параллельной схемой управления версиями и выбором пользователя.  
  
## <a name="unmanaged-vspackages"></a>Неуправляемые пакеты VSPackage  
 Неуправляемый пакет VSPackage — это COM-сервер, который можно установить в любом расположении. Сведения о регистрации должны точно соответствовать его расположению. Пользовательский интерфейс установщика должен предоставлять расположение по умолчанию в качестве подкаталога свойства ProgramFilesFolder установщик Windows. Пример:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\  
  
 Пользователю следует разрешить изменять каталог по умолчанию для размещения пользователей, которые хранят небольшой загрузочный раздел и предпочитают устанавливать приложения и средства на другой том.  
  
 Если ваша Параллельная схема использует пакет VSPackage с версией, можно использовать подкаталоги для хранения разных версий. Пример:  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 ProgramFilesFolder MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Управляемые пакеты VSPackage  
 Управляемые пакеты VSPackage также можно установить в любом расположении. Однако рекомендуется всегда устанавливать их в глобальный кэш сборок (GAC), чтобы сократить время загрузки сборки. Поскольку управляемые пакеты VSPackage всегда являются сборками со строгими именами, их установка в глобальном кэше сборок означает, что их проверка с помощью подписи строгих имен выполняется только во время установки. Сборки со строгими именами, установленные где-либо в файловой системе, должны проверять свои подписи при каждой загрузке. При установке управляемых пакетов VSPackage в глобальный кэш сборок используйте параметр **/Assembly** средства regpkg для записи записей реестра, указывающих на строгое имя сборки.  
  
 Если управляемые пакеты VSPackage устанавливаются в расположении, отличном от GAC, следуйте предыдущему Совету, указанному для неуправляемых пакетов VSPackage, для выбора иерархий каталогов. Используйте параметр **/CodeBase** средства regpkg для записи записей реестра, указывающих на путь сборки VSPackage.  
  
 Дополнительные сведения см. в разделе [Регистрация пакетов VSPackage и их отмена](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>вспомогательные библиотеки DLL  
 По соглашению, вспомогательные DLL VSPackage, которые содержат ресурсы для определенного языкового стандарта, находятся в подкаталогах каталога VSPackage. Подкаталоги соответствуют значениям кода локали (LCID).  
  
 [Управление](../../extensibility/managing-vspackages.md) пакетами VSPackage указывает на то, где [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] на самом деле ищет вспомогательную DLL-библиотеку VSPackage. Однако [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пытается загрузить вспомогательную библиотеку DLL в подкаталог, имя которого имеет значение LCID, в следующем порядке:  
  
1. КОД языка по умолчанию (VS LCID, например, 1033 для английского языка)  
  
2. LCID по умолчанию с подязыковым языком по умолчанию.  
  
3. КОД по умолчанию для системы.  
  
4. Системный LCID по умолчанию с подязыковым языком по умолчанию.  
  
5. Американский английский (. \ 1033 или .\0x409).  
  
   Если библиотека DLL VSPackage содержит ресурсы, а запись реестра Сателлитедлл\дллнаме указывает на него, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пытается загрузить их в указанном порядке.  
  
## <a name="see-also"></a>См. также:  
 [Выбор между общими и версиями пакетов VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)   
 [Регистрация управляемого пакета](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
