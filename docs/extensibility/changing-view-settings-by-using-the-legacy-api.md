---
title: Изменение параметров представления с помощью API прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc0dc26a01cdddb4b26dfa65acab2c497618a76e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106492"
---
# <a name="change-view-settings-by-using-the-legacy-api"></a>Изменение параметров представления с помощью предыдущих версий API
Параметры для основных компонентов редактора, например перенос по словам, поле выделения и виртуального пространства, которые могут быть изменены пользователем с помощью параметра **параметры** диалоговое окно. Тем не менее, можно также изменить эти параметры программным способом.

## <a name="change-settings-by-using-the-legacy-api"></a>Изменение параметров с помощью предыдущих версий API
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Интерфейс предоставляет набор свойств текстового редактора. Представление текста содержит категорию свойств (GUID_EditPropCategory_View_MasterSettings), представляющий группу программно измененных параметров для представления текста. Как только просмотр параметров были изменены таким образом, их нельзя изменить в **параметры** диалоговое окно, пока они переопределены.

 Ниже приведен типичный процесс по изменению параметров представления для экземпляра базового редактора.

1. Вызовите `QueryInterface` на (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, указывая значение GUID_EditPropCategory_View_MasterSettings для `rguidCategory` параметра.

     Это возвращает указатель на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс, который содержит набор свойств, принудительное для представления. Любые параметры в эту группу без возможности восстановления принудительно. Если параметр не является в этой группе, то он будет соответствовать параметры, указанные в **параметры** диалогового окна или команды пользователя.

3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> метод, указывая значение соответствующие параметры в `idprop` параметра.

     Например, чтобы принудительно выполнить перенос по словам, вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> и укажите значение VSEDITPROPID_ViewLangOpt_WordWrap, `vt` для `idprop` параметра. В этом вызове `vt` является РАЗНОВИДНОСТЬЮ VT_BOOL и `vt.boolVal` имеет значение VARIANT_TRUE.

## <a name="reset-changed-view-settings"></a>Сброс изменить параметры представления
 Чтобы сбросить все измененных параметров для экземпляра базовый редактор представления, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> метод и указать значение соответствующий параметр в `idprop` параметра.

 Например, разрешить перенос слов свободно перемещаться, вам нужно удалить его из категории свойства путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> и указав значение VSEDITPROPID_ViewLangOpt_WordWrap для `idprop` параметра.

 Для удаления всех измененных параметров для базового редактора за один раз, укажите значение VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt для `idprop` параметра. В этом вызове vt является РАЗНОВИДНОСТЬЮ VT_BOOL и vt.boolVal имеет значение VARIANT_TRUE.

## <a name="see-also"></a>См. также
- [В редакторе](../extensibility/inside-the-core-editor.md)
- [Представление theText доступ с помощью предыдущих версий API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
- [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md)