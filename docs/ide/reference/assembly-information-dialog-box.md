---
title: Диалоговое окно "Сведения о сборке"
description: Сведения о диалоговом окне "Сведения о сборке" и о том, как оно используется для указания значений для глобальных атрибутов сборки .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d1ed2fd5fe9e49ab947752f84accb326499392fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836426"
---
# <a name="assembly-information-dialog-box"></a>Диалоговое окно "Сведения о сборке"

Диалоговое окно "Сведения о сборке" используется для указания значений глобальных атрибутов сборки .NET Framework, хранящихся в файле AssemblyInfo, который автоматически создается в проекте. У проектов Visual Basic этот файл находится в узле **Мой проект** в обозревателе решений (чтобы увидеть его, щелкните **Показать все файлы**). У проектов C# он находится в разделе **Свойства**. Дополнительные сведения см. в разделе [Атрибуты (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Чтобы открыть это диалоговое окно, выберите узел проекта в **обозревателе решений**, а затем в меню **Проект** выберите пункт **Свойства**. На странице **Приложение** нажмите кнопку **Сведения о сборке**.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса

**Заголовок**\
Указывает заголовок для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTitleAttribute>.

**Описание**\
Указывает дополнительное описание для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Компания**\
Указывает имя организации для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCompanyAttribute>.

Вы можете задать или изменить значение по умолчанию для компании в реестре. Найдите значение **RegisteredOrganization** в разделе реестра **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** или **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** в зависимости от используемой версии Windows.

**Продукт**\
Указывает имя продукта для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyProductAttribute>.

**Авторское право**\
Указывает авторские права для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Товарный знак**\
Указывает товарный знак для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Версия сборки**\
Задает версию сборки. Соответствует <xref:System.Reflection.AssemblyVersionAttribute>.

**Версия файла**\
Дает компилятору указание использовать определенный номер версии для ресурса версии файла Win32. Соответствует <xref:System.Reflection.AssemblyFileVersionAttribute>.

**GUID**\
Уникальный идентификатор GUID для сборки. При создании проекта Visual Studio создает идентификатор GUID для сборки. Соответствует <xref:System.Guid>.

**Нейтральный язык**\
Указывает, какой язык и региональные параметры поддерживает сборка. Соответствует <xref:System.Resources.NeutralResourcesLanguageAttribute>. Значение по умолчанию — **(Нет)** .

**Сделать сборку видимой для COM**\
Указывает, будут ли типы в сборке доступными для модели COM. Соответствует <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Дополнительные сведения об установке этих свойств при создании пакета NuGet в библиотеке классов .NET Framework см. в разделе [Настройка свойств проекта для пакета](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>См. также раздел

- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Атрибуты](/previous-versions/z0w1kczw(v=vs.140))