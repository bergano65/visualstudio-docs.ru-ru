---
title: Изменение параметров представления с помощью API прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddca5f9159c2cb20eeb8525bd37730a88f64fb43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990353"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Изменение параметров представления с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметры для основных компонентов редактора, например перенос по словам, поле выделения и виртуального пространства, которые могут быть изменены пользователем с помощью параметра **параметры** диалоговое окно. Тем не менее, можно также изменить эти параметры программным способом.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Изменение параметров с помощью API прежних версий  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Интерфейс предоставляет набор свойств текстового редактора. Представление текста содержит категорию свойств (GUID_EditPropCategory_View_MasterSettings), представляющий группу программно измененных параметров для представления текста. Как только просмотр параметров были изменены таким образом, их нельзя изменить в **параметры** диалоговое окно, пока они переопределены.  
  
 Ниже приведен типичный процесс по изменению параметров представления для экземпляра базового редактора.  
  
1.  Вызовите `QueryInterface` на (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, указывая значение GUID_EditPropCategory_View_MasterSettings для `rguidCategory` параметра.  
  
     Это возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс, который содержит набор свойств, принудительное для представления. Любые параметры в эту группу без возможности восстановления принудительно. Если параметр не является в этой группе, то он будет соответствовать параметры, указанные в **параметры** диалогового окна или команды пользователя.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> метод, указывая значение соответствующие параметры в `idprop` параметра.  
  
     Например, чтобы принудительно выполнить перенос по словам, вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> и укажите значение VSEDITPROPID_ViewLangOpt_WordWrap, `vt` для `idprop` параметра. В этом вызове `vt` является РАЗНОВИДНОСТЬЮ VT_BOOL и `vt.boolVal` имеет значение VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Сброс параметров представления  
 Чтобы сбросить все измененных параметров для экземпляра базовый редактор представления, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> метод и указать значение соответствующий параметр в `idprop` параметра.  
  
 Например, разрешить перенос слов свободно перемещаться, вам нужно удалить его из категории свойства путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> и указав значение VSEDITPROPID_ViewLangOpt_WordWrap для `idprop` параметра.  
  
 Для удаления всех измененных параметров для базового редактора за один раз, укажите значение VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt для `idprop` параметра. В этом вызове vt является РАЗНОВИДНОСТЬЮ VT_BOOL и vt.boolVal имеет значение VARIANT_TRUE.  
  
## <a name="see-also"></a>См. также  
 [В редакторе](../extensibility/inside-the-core-editor.md)   
 [Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md)
