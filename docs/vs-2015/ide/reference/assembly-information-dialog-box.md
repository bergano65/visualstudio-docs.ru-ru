---
title: Диалоговое окно "Сведения о сборке" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbcc8f31d00c270cf0eb9af8d3283a8674a639e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703707"
---
# <a name="assembly-information-dialog-box"></a>Диалоговое окно "Сведения о сборке"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Диалоговое окно **Сведения о сборке** используется для указания значений глобальных атрибутов сборки [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], хранящихся в файле AssemblyInfo, который автоматически создается в проекте. В **обозревателе решений** этот файл находится в узле **Мой проект** в [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (чтобы увидеть его, щелкните **Показать все файлы**), а именно, в разделе **Свойства** в [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Подробнее об атрибутах сборки см. в разделе [Атрибуты](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Чтобы открыть это диалоговое окно, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. После того как откроется **конструктор проектов**, перейдите на вкладку **Приложение**. На странице **Приложение** нажмите кнопку **Сведения о сборке**.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Заголовок**  
 Указывает заголовок для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Описание**  
 Указывает дополнительное описание для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Компания**  
 Указывает имя организации для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Продукт**  
 Указывает имя продукта для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Авторские права**  
 Указывает авторские права для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Товарный знак**  
 Указывает товарный знак для манифеста сборки. Соответствует <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Версия сборки**  
 Задает версию сборки. Соответствует <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Версия файла**  
 Дает компилятору указание использовать определенный номер версии для ресурса версии файла Win32. Соответствует <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Уникальный идентификатор GUID для сборки. При создании проекта Visual Studio создает идентификатор GUID для сборки. Соответствует <xref:System.Guid>.  
  
 **Нейтральный язык**  
 Указывает, какой язык и региональные параметры поддерживает сборка. Соответствует <xref:System.Resources.NeutralResourcesLanguageAttribute>. Значение по умолчанию — **(Нет)**.  
  
 **Сделать сборку видимой для COM**  
 Указывает, будут ли типы в сборке доступными для модели COM. Соответствует <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>См. также раздел  
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Атрибуты](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
