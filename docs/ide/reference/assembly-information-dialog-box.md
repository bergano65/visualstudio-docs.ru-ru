---
title: Диалоговое окно "Сведения о сборке"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c5420839d97fb62797d0f739ce62da4d14b340b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744881"
---
# <a name="assembly-information-dialog-box"></a>Диалоговое окно "Сведения о сборке"
**Сведения о сборке** диалоговое окно используется для указания значений атрибутов глобальной сборки .NET Framework, которые хранятся в файле AssemblyInfo, автоматически создается в проекте. В **обозревателе решений** этот файл находится в узле **Мой проект** в [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (чтобы увидеть его, щелкните **Показать все файлы**), а именно, в разделе **Свойства** в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Подробнее об атрибутах сборки см. в разделе [Атрибуты](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Чтобы открыть это диалоговое окно, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. После того как откроется **конструктор проектов**, перейдите на вкладку **Приложение**. На странице **Приложение** нажмите кнопку **Сведения о сборке**.

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса
 **Заголовок** Указывает заголовок для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTitleAttribute>.

 **Описание** Указывает дополнительное описание для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Организация** Указывает имя организации для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Продукт** Указывает имя продукта для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyProductAttribute>.

 **Авторские права** Указывает авторские права для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Товарный знак** Указывает товарный знак для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Версия сборки** Указывает версию сборки, которой присваиваются атрибуты. Соответствует <xref:System.Reflection.AssemblyVersionAttribute>.

 **Версия файла** Дает компилятору указание использовать определенный номер версии для ресурса версии файла Win32. Соответствует <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** Уникальный идентификатор GUID для сборки. При создании проекта Visual Studio создает идентификатор GUID для сборки. Соответствует <xref:System.Guid>.

 **Нейтральный язык** Указывает, какой язык и региональные параметры поддерживает сборка. Соответствует <xref:System.Resources.NeutralResourcesLanguageAttribute>. Значение по умолчанию — **(Нет)** .

 **Сделать сборку видимой для COM** Указывает, будут ли типы в сборке доступными для модели COM. Соответствует <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>См. также раздел

- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Атрибуты](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)