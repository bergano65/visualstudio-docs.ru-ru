---
title: Изменение параметров представления с помощью прежних версий API | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc68bf5f8a0e61b80200cd5454b78bcdda78cdfe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Изменение параметров представления с помощью API прежних версий
Параметры основных функций редактора, например перенос по словам, выделения и виртуальное пространство, которые могут быть изменены пользователем с помощью параметра **параметры** диалоговое окно. Однако это также можно изменить эти параметры программным образом.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Изменение параметров с помощью API прежних версий  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Интерфейс предоставляет набор свойств текстового редактора. Текстовое представление содержит категорию свойств (GUID_EditPropCategory_View_MasterSettings), представляющее группу программно измененные параметры для представления текста. После настройки представления были изменены таким образом, их нельзя изменить в **параметры** диалоговое окно «», пока они переопределены.  
  
 Ниже приведен типичный процесс изменения параметров представления для экземпляра базового редактора.  
  
1.  Вызовите `QueryInterface` на (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейса.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, указывая значение GUID_EditPropCategory_View_MasterSettings для `rguidCategory` параметра.  
  
     Таким образом возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс, содержащий набор свойств принудительного для представления. Все параметры в этой группе постоянно принудительно. Если параметр не входит в эту группу, то она будет следовать параметры, указанные в **параметры** диалогового окна или команды пользователя.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> метод, указывая значение соответствующие параметры в `idprop` параметра.  
  
     Например, чтобы принудительно выполнить перенос по словам, вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> и укажите значение VSEDITPROPID_ViewLangOpt_WordWrap, `vt` для `idprop` параметра. В этом вызове `vt` является РАЗНОВИДНОСТЬЮ VT_BOOL и `vt.boolVal` имеет значение VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Сброс параметров представления  
 Чтобы сбросить все измененных параметров для экземпляра базового редактора просмотра, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> метод и указать значение соответствующего параметра в `idprop` параметра.  
  
 Например, разрешить свободно перемещаться по словам, вам нужно удалить его из категории свойств путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> и указав значение VSEDITPROPID_ViewLangOpt_WordWrap для `idprop` параметра.  
  
 Чтобы удалить все измененные параметры для базового редактора, укажите значение VSEDITPROPID_ViewComposite_AllCodeWindowDefaults vt для `idprop` параметра. В этом вызове vt является РАЗНОВИДНОСТЬЮ VT_BOOL и vt.boolVal имеет значение VARIANT_TRUE.  
  
## <a name="see-also"></a>См. также  
 [В редакторе Core](../extensibility/inside-the-core-editor.md)   
 [Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md)