---
title: Выбор каталога установки для VSPackage | Документация Майкрософт
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
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385877b8a682574946bfd43e1e51acd771d00a2b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775177"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Выбор каталога установки для VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage и ее вспомогательные файлы должны находиться в файловой системе пользователя. Расположение зависит ли VSPackage является управляемым или неуправляемым, схема управления версиями side-by-side и выбор пользователя.  
  
## <a name="unmanaged-vspackages"></a>Неуправляемые пакеты VSPackage  
 Неуправляемого VSPackage — это сервер COM, который может быть установлен в любом месте. Сведения о его регистрации необходимо точно отражает его расположение. Установщик пользовательский интерфейс (UI) следует указать расположение по умолчанию как подкаталог свойства установщика Windows ProgramFilesFolder. Пример:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 Пользователь должны изменить каталог по умолчанию для пользователей, сохранить небольшой загрузочный раздел и для установки приложения и средства на другом томе.  
  
 Если схему side-by-side использует VSPackage с версиями, можно использовать вложенные папки для хранения различных версий. Пример:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Управляемые пакеты VSPackage  
 Управляемые пакеты VSPackage также можно установить в любом месте. Тем не менее следует всегда устанавливаться в глобальный кэш сборок (GAC), чтобы сократить время загрузки сборки. Так как управляемые пакеты VSPackage, всегда являются строгими, их установки в глобальном кэше СБОРОК означает, что их проверка подписи строгого имени принимает только во время установки. Сборки со строгими именами, установленные в других местах в файловой системе, должны иметь их подписи, проверить каждый раз, чтобы они были загружены. При установке управляемые пакеты VSPackage в глобальном кэше СБОРОК, используйте средство regpkg **/Assembly** переключиться в режим записи реестра, указывающий на строгое имя сборки.  
  
 При установке управляемые пакеты VSPackage в расположение, отличное от глобального кэша СБОРОК, следуйте предыдущему совету, заданными для неуправляемые пакеты VSPackage, по выбору иерархий каталогов. Используйте средство regpkg **/ codebase** переключиться в режим записи реестра, указывающий на путь к сборке VSPackage.  
  
 Дополнительные сведения см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Вспомогательные библиотеки DLL  
 По соглашению VSPackage вспомогательные библиотеки DLL, которые содержат ресурсы для конкретного языкового стандарта — находятся в подкаталоги каталога VSPackage. Подкаталоги соответствуют значениям идентификатор (LCID) языка.  
  
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md) указывает, что записи реестра управляет where [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] фактически выполняет поиск объекта VSPackage, вспомогательные библиотеки DLL. Тем не менее [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пытается загрузить вспомогательную библиотеку DLL в подкаталог с именем для значения кода языка, в следующем порядке:  
  
1. По умолчанию код языка (LCID VS \1033 например для английского языка)  
  
2. Код языка по умолчанию с помощью варианта по умолчанию.  
  
3. Системное значение по умолчанию код языка.  
  
4. Системы по умолчанию код языка с помощью варианта по умолчанию.  
  
5. США Английский (. \1033 или. \0x409).  
  
   Если библиотека DLL VSPackage содержит ресурсы и точки входа реестра SatelliteDll\DllName, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пытается загрузить их в списке выше.  
  
## <a name="see-also"></a>См. также  
 [Выбор между общих и с контролем версий пакетов VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)   
 [Регистрация управляемых пакетов](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

