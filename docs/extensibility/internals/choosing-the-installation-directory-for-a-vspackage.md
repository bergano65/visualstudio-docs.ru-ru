---
title: Выбор каталога установки для VSPackage (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709760"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Выберите каталог установки для VSPackage
VSPackage и его вспомогательные файлы должны быть в файловой системе пользователя. Местоположение зависит от того, управляется ли VSPackage или неуправляемым, от вашей схемы бок о бок и выбора пользователя.

## <a name="unmanaged-vspackages"></a>Неуправляемые VSPackages
 Неуправляемый VSPackage — это com-сервер, который может быть установлен в любом месте. Его регистрационная информация должна точно отражать его местоположение. Пользовательский интерфейс установки (UI) должен предоставлять местоположение по `ProgramFilesFolder` умолчанию в качестве субдиректора значения свойства установки Windows. Пример:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;NoV1.0\\*

 Пользователю должно быть разрешено изменять каталог по умолчанию, чтобы разместить пользователей, которые держат небольшую раздел загрузки и предпочитают устанавливать приложения и инструменты на другой том.

 Если ваша схема использует версию VSPackage, вы можете использовать субдиректора для хранения различных версий. Пример:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Управляемые пакеты VSPackage
 Управляемые VSPackages также могут быть установлены в любом месте. Однако следует рассмотреть возможность установки их в глобальный кэш сборки (GAC) для сокращения времени загрузки сборки. Поскольку управляемые VSPackages всегда являются сильными сборками, установка их в GAC означает, что их проверка подписи с сильным именем занимает только во время установки. Сильные сборки, установленные в других частях файловой системы, должны проверять свои подписи каждый раз, когда они загружаются. При установке управляемых VSPackages в GAC используйте переключатель **regpkg's/assembly** для записи записей реестра, указывающих на сильное имя сборки.

 Если вы устанавливаете управляемые VSPackages в другом месте, кроме GAC, следуйте ранее рекомендациям, предоставленным для неуправляемых VSPackages для выбора иерархий каталогов. Используйте переключатель **regpkg's/codebase** для записи записей реестра, указывающих на путь сборки VSPackage.

 Для получения дополнительной информации, см [Регистрация и отменить регистрацию VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>вспомогательные библиотеки DLL
 По конвенции, спутник DLL VSPackage, которые содержат ресурсы для определенного места, расположены в субдиректорах каталога *VSPackage.* Субдиректори соответствуют значениям locale ID (LCID).

 [Управление VSPackages](../../extensibility/managing-vspackages.md) статья указывает на то, что реестр записей управления, где [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] на самом деле ищет спутник анализировать VSPackage DLL. Тем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не менее, пытается загрузить спутник DLL в субдиректории, названной в честь значения LCID, в следующем порядке:

1. По умолчанию LCID (Visual Studio LCID; например, *1033 евро* для английского языка)

2. По умолчанию LCID с субязыком по умолчанию.

3. Система по умолчанию LCID.

4. Система по умолчанию LCID с субязыком по умолчанию.

5. Английский язык США *(. .* . . *.*. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

Если ваш VSPackage DLL включает в себя ресурсы и точки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] входа в реестр **SatelliteDll'DllName,** попытайтесь загрузить их в вышеуказанном порядке.

## <a name="see-also"></a>См. также
- [Выбирайте между общими и версиями VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
- [Управление регистрацией пакетов](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
