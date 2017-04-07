---
title: "Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools 2017 | Документация Майкрософт"
description: "Идентификаторы рабочих нагрузок и компонентов Visual Studio можно использовать для создания классических приложений Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 230d04f93e8e857fc0dbaf018e56567259ac6c38
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Каталог компонентов для Visual Studio Build Tools 2017

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты. По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>MSBuild Tools

**Идентификатор.** Microsoft.VisualStudio.Workload.MSBuildTools

**Описание.** Предоставляет средства для сборки приложений на основе MSBuild.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Обязательное
Microsoft.VisualStudio.Component.CoreBuildTools | Ядро Visual Studio Build Tools | Обязательное
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | Обязательное


## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**Идентификатор.** Microsoft.VisualStudio.Workload.VCTools

**Описание.** Создание классических приложений для Windows с помощью набора инструментов Visual C++, библиотеки ATL и дополнительных средств, таких как MFC и C++/CLI.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Основные возможности Visual C++ Build Tools | Обязательное
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | Обязательное
Microsoft.VisualStudio.Component.VC.CMake.Project | Инструменты Visual C++ для CMake | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | Рекомендованное
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | Optional
Microsoft.VisualStudio.Component.VC.ATL | Поддержка библиотеки ATL для Visual C++ | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Поддержка библиотек MFC и ATL (x86 и x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (экспериментальная версия) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Основные компоненты Visual Studio C++ | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули стандартных библиотек | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | Optional


## <a name="web-development-build-tools"></a>Средства сборки для веб-разработчиков

**Идентификатор.** Microsoft.VisualStudio.Workload.WebBuildTools

**Описание.** Задачи и целевые объекты MSBuild для построения веб-приложений.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | Имя | Тип зависимости
--- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Средства сборки для веб-разработчиков | Обязательное
## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | Имя
--- | ---
Н/Д | Н/Д


## <a name="see-also"></a>См. также

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)

