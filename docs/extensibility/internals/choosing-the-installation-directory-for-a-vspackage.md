---
title: Выбор каталога установки для пакетов VSPackage | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134448"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Выбор каталога установки для пакетов VSPackage
Пакет VSPackage и ее вспомогательные файлы должны быть в файловой системе пользователя. Расположение зависит ли VSPackage управляемого или неуправляемого схемы управления версиями side-by-side и выбор пользователя.  
  
## <a name="unmanaged-vspackages"></a>Неуправляемые пакеты VSPackage  
 Неуправляемого VSPackage является COM-сервера, который может быть установлен в любом месте. Регистрационные сведения должны точно отражает его расположение. Установщик пользовательского интерфейса (UI) должен предоставить место по умолчанию, где подкаталог свойство ProgramFilesFolder установщика Windows. Пример:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\  
  
 Пользователю должно быть разрешено изменить каталог по умолчанию для пользователей, сохранить небольшой загрузочный раздел и выбрать предпочтительные для установки приложений и средств на другом томе.  
  
 Если свою схему side-by-side использует VSPackage с версиями, можно использовать вложенные папки для хранения различных версий. Пример:  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder] MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Управляемые пакеты VSPackage  
 Управляемые пакеты VSPackage также можно установить в любом месте. Однако следует всегда устанавливаться в глобальный кэш сборок (GAC), чтобы сократить время загрузки сборки. Так как управляемые пакеты VSPackage всегда сборки со строгими именами, их установки в глобальном кэше СБОРОК означает, что их проверка подписи строгого имени принимает только во время установки. Сборки со строгими именами, установленные в других местах, в файловой системе, должны иметь их подписи, проверить каждый раз, они загружаются. При установке управляемые пакеты VSPackage в глобальном кэше СБОРОК, используйте средство regpkg **/Assembly** коммутатора для записи реестра, указывающий строгое имя сборки.  
  
 Если установить управляемые пакеты VSPackage в расположении, отличном от глобального кэша СБОРОК, следуйте предыдущему совету заданных неуправляемые пакеты VSPackage по выбору иерархии каталога. Используйте средство regpkg **/ codebase** коммутатора для записи реестра, указав путь сборки VSPackage.  
  
 Дополнительные сведения см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Вспомогательные библиотеки DLL  
 По соглашению VSPackage вспомогательные библиотеки DLL — которой содержат ресурсы для конкретного языка, находящиеся во вложенных каталогах каталога VSPackage. Подкаталоги соответствуют значениям идентификатор (LCID) языка.  
  
 [Управление пакетов VSPackage](../../extensibility/managing-vspackages.md) указывает, что записи реестра элемент управления, где [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] фактически выполняет поиск в пакете VSPackage вспомогательного DLL-файла. Тем не менее [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пытается загрузить вспомогательную библиотеку DLL в подкаталог для значения кода языка, в следующем порядке:  
  
1.  По умолчанию код языка (LCID VS \1033 например для английского языка)  
  
2.  Код языка по умолчанию с помощью варианта по умолчанию.  
  
3.  Системное значение по умолчанию код языка.  
  
4.  Системы по умолчанию код языка с варианта по умолчанию.  
  
5.  США Английский (. \1033 или. \0x409).  
  
 Если библиотеки DLL VSPackage содержит ресурсы и точки входа реестра SatelliteDll\DllName, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пытается загрузить их в порядке, приведенном выше.  
  
## <a name="see-also"></a>См. также  
 [Выбор между общих и с версией пакетов VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Управление пакетов VSPackage](../../extensibility/managing-vspackages.md)   
 [Регистрация управляемых пакетов](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)