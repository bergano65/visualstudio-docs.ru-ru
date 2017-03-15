---
title: "Диалоговое окно &quot;Сведения о сборке&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 1a215cb25c14137f1ccc535833261a5bfc5f7a02
ms.lasthandoff: 02/22/2017

---
# <a name="assembly-information-dialog-box"></a>Диалоговое окно "Сведения о сборке"
Диалоговое окно **Сведения о сборке** используется для указания значений глобальных атрибутов сборки [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], хранящихся в файле AssemblyInfo, который автоматически создается в проекте. В **обозревателе решений** этот файл находится в узле **Мой проект** в [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (чтобы увидеть его, щелкните **Показать все файлы**), а именно, в разделе **Свойства** в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Подробнее об атрибутах сборки см. в разделе [Атрибуты](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Чтобы открыть это диалоговое окно, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. После того как откроется **конструктор проектов**, перейдите на вкладку **Приложение**. На странице **Приложение** нажмите кнопку **Сведения о сборке**.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Заголовок**  
 Указывает заголовок для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Описание**  
 Указывает дополнительное описание для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Компания**  
 Указывает имя организации для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Продукт**  
 Указывает имя продукта для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Авторские права**  
 Указывает авторские права для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Товарный знак**  
 Указывает товарный знак для манифеста сборки. Соответствует значению <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Версия сборки**  
 Задает версию сборки. Соответствует значению <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Версия файла**  
 Дает компилятору указание использовать определенный номер версии для ресурса версии файла Win32. Соответствует значению <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Уникальный идентификатор GUID для сборки. При создании проекта Visual Studio создает идентификатор GUID для сборки. Соответствует значению <xref:System.Guid>.  
  
 **Нейтральный язык**  
 Указывает, какой язык и региональные параметры поддерживает сборка. Соответствует значению <xref:System.Resources.NeutralResourcesLanguageAttribute>. Значение по умолчанию — **(Нет)**.  
  
 **Сделать сборку видимой для COM**  
 Указывает, будут ли типы в сборке доступными для модели COM. Соответствует значению <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Атрибуты](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
