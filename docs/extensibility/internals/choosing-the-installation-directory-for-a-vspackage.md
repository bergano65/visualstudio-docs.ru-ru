---
title: Выбор каталога установки для VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a5016c528e754e452ee1248e85b705c41a44ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621075"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Выберите каталог установки для VSPackage
VSPackage и ее вспомогательные файлы должны находиться в файловой системе пользователя. Расположение зависит ли VSPackage является управляемым или неуправляемым, схема управления версиями side-by-side и выбор пользователя.

## <a name="unmanaged-vspackages"></a>Неуправляемые пакеты VSPackage
 Неуправляемого VSPackage — это сервер COM, который может быть установлен в любом месте. Сведения о его регистрации должно точно отражать его расположение. Пользовательский интерфейс (UI) установщик должен предоставить расположение по умолчанию как подкаталог `ProgramFilesFolder` значение свойства установщика Windows. Пример:

*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*

 Пользователь должны изменить каталог по умолчанию для пользователей, сохранить небольшой загрузочный раздел и для установки приложения и средства на другом томе.

 Если схему side-by-side использует VSPackage с версиями, можно использовать вложенные папки для хранения различных версий. Пример:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002 г.\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Управляемые пакеты VSPackage
 Управляемые пакеты VSPackage также можно установить в любом месте. Тем не менее следует всегда устанавливаться в глобальный кэш сборок (GAC), чтобы сократить время загрузки сборки. Так как управляемые пакеты VSPackage, всегда являются строгими, их установки в глобальном кэше СБОРОК означает, что их проверка подписи строгого имени принимает только во время установки. Сборки со строгими именами, установленные в других местах в файловой системе, должны иметь их подписи, проверить каждый раз, чтобы они были загружены. При установке управляемые пакеты VSPackage в глобальном кэше СБОРОК, используйте средство regpkg **/Assembly** переключиться в режим записи реестра, указывающий на строгое имя сборки.

 При установке управляемые пакеты VSPackage в расположение, отличное от глобального кэша СБОРОК, следуйте предыдущему совету, заданными для неуправляемые пакеты VSPackage, по выбору иерархий каталогов. Используйте средство regpkg **/ codebase** переключиться в режим записи реестра, указывающий на путь к сборке VSPackage.

 Дополнительные сведения см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Вспомогательные библиотеки DLL
 По соглашению VSPackage вспомогательные библиотеки DLL, содержащие ресурсы для конкретного языкового стандарта, находятся в подкаталогах *VSPackage* каталога. Подкаталоги соответствуют значениям идентификатор (LCID) языка.

 [Управления пакеты VSPackage](../../extensibility/managing-vspackages.md) статье указывает, что записи реестра управляет where [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] фактически выполняет поиск объекта VSPackage, вспомогательные библиотеки DLL. Тем не менее [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пытается загрузить вспомогательную библиотеку DLL в подкаталог с именем для значения кода языка, в следующем порядке:

1.  По умолчанию код языка (Visual Studio LCID, например *\1033* для английского языка)

2.  Код языка по умолчанию с помощью варианта по умолчанию.

3.  Системное значение по умолчанию код языка.

4.  Системы по умолчанию код языка с помощью варианта по умолчанию.

5.  США Английский (*. \1033* или *. \0x409*).


Если библиотека DLL VSPackage содержит ресурсы и **SatelliteDll\DllName** запись реестра указывает на нее, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пытается загрузить их в списке выше.

## <a name="see-also"></a>См. также
- [Выбор между общих и с контролем версий пакетов VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Управление пакетов VSPackage](../../extensibility/managing-vspackages.md)
- [Управление регистрацией пакетов](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)