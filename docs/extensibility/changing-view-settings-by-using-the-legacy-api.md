---
title: "Изменение параметров представления с помощью API прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - изменение параметров представления"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Изменение параметров представления с помощью API прежних версий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметры функций редактора, как перенос по словам, поле выделения и виртуальное пространство, могут быть изменены пользователем посредством **Параметры** диалоговое окно.  Однако можно также изменять эти параметры.  
  
## Изменение параметров с использованием традиционного API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс предоставляет набор свойств текстового редактора.  Представление текста, содержащий категорию свойств \(GUID\_EditPropCategory\_View\_MasterSettings\), которая представляет группу в составе программно изменены параметры для представления текста.  После настройки представления было изменено таким образом, они не могут быть изменены в **Параметры** диалоговое окно до тех пор, пока они не сброшены.  
  
 Ниже приведен типичный процесс для изменения параметров представления для экземпляра редактора.  
  
1.  Вызов `QueryInterface` on \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\)  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, указав значение для GUID\_EditPropCategory\_View\_MasterSettings  `rguidCategory` параметр.  
  
     Это возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс, который содержит набор forced свойств для представления.  Все параметры в этой группе окончательно принудятся.  Если параметр отсутствует в этой группе, то его следует параметрами, определенными в **Параметры** диалоговое окно или группы пользователей.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> метод, указав соответствующее значение параметров  `idprop` параметр.  
  
     Например, принудительно перенос по словам, вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> и укажите значение VSEDITPROPID\_ViewLangOpt\_WordWrap,  `vt` для  `idprop` параметр.  В этом вызове `vt` ВАРИАНТ типа и VT\_BOOL  `vt.boolVal` VARIANT\_TRUE.  
  
## Сбросить измененные параметры вид  
 Чтобы сбросить любой измененный параметр представления для экземпляра редактора, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> метод и определяет подходящее значение параметра  `idprop` параметр.  
  
 Например, чтобы включить перенос по словам для плыть свободно, удалитьTfи мере его из категорий свойства путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> и указав значение для VSEDITPROPID\_ViewLangOpt\_WordWrap  `idprop` параметр.  
  
 Чтобы удалить все измененные параметры для редактора core одновременно, укажите значение для VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults, vt `idprop` параметр.  В этом вызове, vt ВАРИАНТ типа VT\_BOOL и vt.boolVal VARIANT\_TRUE.  
  
## См. также  
 [В редакторе ядра](../extensibility/inside-the-core-editor.md)   
 [Доступ к theText представление с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md)