---
title: "Диалоговое окно &quot;Сведения о сборке&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAssemblyInfo"
helpviewer_keywords: 
  - "Диалоговое окно "Сведения о сборке""
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Диалоговое окно &quot;Сведения о сборке&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Диалоговое окно **Сведения о сборке** используется для указания значений глобальных атрибутов сборки [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], хранящихся в файле AssemblyInfo, который автоматически создается вместе с проектом.  В **Обозревателе решений** файл расположен в узле **Мой проект** в [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] \(нажмите **Показать все файлы**, чтобы просмотреть\); который находится в окне **Свойства** в [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Дополнительные сведения об атрибутах сборки см. в разделе [Атрибуты](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Чтобы открыть это диалоговое окно, выберите узел проекта в **Обозревателе решений** и затем в меню **Проект** выберите команду **Свойства**.  После того как откроется **Конструктор проектов**, перейдите на вкладку **Приложение**.  На странице **Приложение** нажмите кнопку **Сведения о сборке**.  
  
## Список элементов пользовательского интерфейса  
 **Заголовок**  
 Указывает название манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Описание**  
 Указывает необязательное описание манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Компания**  
 Указывает название компании для манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Продукт**  
 Указывает название продукта для манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Сведения об авторском праве**  
 Указывает сведения об авторском праве для манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Товарный знак**  
 Указывает товарный знак для манифеста сборки.  Соответствует параметру <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Версия сборки**  
 Задает версию сборки.  Соответствует параметру <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Версия файла.**  
 Задает компилятору инструкцию использовать определенный номер версии для ресурса версии файла Win32.  Соответствует параметру <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Уникальный идентификатор \(GUID\) сборки.  При создании проекта в среде Visual Studio автоматически генерируется идентификатор GUID для сборки.  Соответствует параметру <xref:System.Guid>.  
  
 **Нейтральный язык**  
 Определяет, какие язык и региональные параметры поддерживает сборка.  Соответствует параметру <xref:System.Resources.NeutralResourcesLanguageAttribute>.  Значение по умолчанию — **\(Нет\)**.  
  
 **Предоставить модели COM доступ к сборке**  
 Указывает, будут ли типы в сборке доступными для модели COM.  Соответствует параметру <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## См. также  
 [Страница «Приложение» в конструкторе проектов \(Visual Basic\)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Атрибуты](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)