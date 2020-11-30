---
title: Страница свойств приложения для приложений UWP
description: Сведения о том, как с помощью страницы "Приложение" указать сведения о сборке и пакете для проекта универсальной платформы Windows (UWP), а также версии целевой платформы Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 826d408d8e1a6a2cb8bcad956ce930781a9155db
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871370"
---
# <a name="application-property-page-uwp-projects"></a>Страница свойств приложения (проекты UWP)

Страница свойств **Приложение** позволяет выбрать параметры сборки и пакетов для универсальной платформы Windows (UWP), а также версию целевой платформы Windows 10.

![Страница свойств приложения](media/application-page-uwp.png)

Чтобы получить доступ к странице **Приложение**, выберите узел проекта **обозревателе решений**. Затем в строке меню выберите **Проект** > **Свойства**. На вкладке **Приложение** откроется страница свойств.

## <a name="general-section"></a>Общий раздел

**Имя сборки**&mdash;Определяет имя выходного файла, который будет содержать манифест сборки.

Для программного доступа к этому свойству см. раздел <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Пространство имен по умолчанию**&mdash;Определяет базовое пространство имен для файлов, добавляемых в проект. Дополнительные сведения о пространствах имен см. в статьях [Пространства имен (Руководство по программированию в C#)](/dotnet/csharp/programming-guide/namespaces/), [Namespaces (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) (Пространства имен в Visual Basic) или [Namespaces (C++)](/cpp/cpp/namespaces-cpp) (Пространства имен в C++).

Для программного доступа к этому свойству см. раздел <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Сведения о сборке**&mdash;Нажмите эту кнопку, чтобы открыть диалоговое окно [Сведения о сборке](../../ide/reference/assembly-information-dialog-box.md).

**Манифест пакета**&mdash;Эта кнопка открывает конструктор манифеста. Также конструктор манифеста можно вызвать, выбрав файл _Package.appxmanifest_ в **обозревателе решений**. Дополнительные сведения см. в разделе [Настройка пакета с помощью конструктора манифестов](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Раздел определения цели

Вы можете указать для приложения целевую версию и минимально допустимую версию Windows 10, используя раскрывающиеся списки в этом разделе. Рекомендуем указывать в качестве целевой последнюю версию Windows 10, а для корпоративных приложений поддерживать и более старую минимальную версию. Дополнительные сведения о выборе версий Windows 10 вы найдете в статье [Выбор версии UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Сведения о выборе целевых платформ в Visual Studio см. в разделе [Целевая платформа](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>См. также раздел

- [Создание первого приложения](/windows/uwp/get-started/your-first-app)
- [Выбор версии UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
