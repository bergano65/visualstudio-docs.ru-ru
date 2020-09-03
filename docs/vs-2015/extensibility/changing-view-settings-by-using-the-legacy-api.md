---
title: Изменение параметров представления с помощью устаревшего API | Документация Майкрософт
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
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184468"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Изменение параметров представления с помощью API прежних версий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметры для основных функций редактора, таких как перенос по словам, поля выбора и виртуальное пространство, могут быть изменены пользователем с помощью диалогового окна " **Параметры** ". Однако эти параметры также можно изменить программным способом.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Изменение параметров с помощью API прежних версий  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>Интерфейс предоставляет набор свойств текстового редактора. Текстовое представление содержит категорию свойств (GUID_EditPropCategory_View_MasterSettings), которая представляет группу программно измененных параметров для текстового представления. Когда параметры представления были изменены таким образом, их нельзя изменить в диалоговом окне **Параметры** до тех пор, пока они не будут сброшены.  
  
 Ниже приведен типичный процесс изменения параметров представления для экземпляра базового редактора.  
  
1. Вызовите метод `QueryInterface` в ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейса.  
  
2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, указав значение GUID_EditPropCategory_View_MasterSettings для `rguidCategory` параметра.  
  
     При этом возвращается указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс, который содержит набор принудительных свойств для представления. Все параметры в этой группе постоянно принудительно выполняются. Если параметр отсутствует в этой группе, то он будет следовать параметрам, указанным в диалоговом окне **Параметры** или в командах пользователя.  
  
3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> метод, указав соответствующие значения параметров в `idprop` параметре.  
  
     Например, чтобы принудительно выполнить перенос по словам, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> и укажите значение VSEDITPROPID_ViewLangOpt_WordWrap `vt` для `idprop` параметра. В этом вызове `vt` является вариантом типа VT_BOOL и `vt.boolVal` VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Сброс параметров измененного представления  
 Чтобы сбросить параметры измененного представления для экземпляра базового редактора, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> метод и укажите соответствующее значение параметра в `idprop` параметре.  
  
 Например, чтобы обеспечить свободный перенос по словам, удалите его из категории свойств, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> и указав значение VSEDITPROPID_ViewLangOpt_WordWrap для `idprop` параметра.  
  
 Чтобы удалить все измененные параметры для базового редактора одновременно, укажите значение VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT для `idprop` параметра. В этом вызове VT является РАЗНОВИДНОСТью типа VT_BOOL а VT. Булвал — VARIANT_TRUE.  
  
## <a name="see-also"></a>См. также:  
 [Внутри основного редактора](../extensibility/inside-the-core-editor.md)   
 [Доступ к представлению Сетекст с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md)
