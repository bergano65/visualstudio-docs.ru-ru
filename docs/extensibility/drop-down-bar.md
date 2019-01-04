---
title: Раскрывающийся список | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a23249a80b87c55e3065abb7cca192182aad4fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968067"
---
# <a name="drop-down-bar"></a>Раскрывающийся список
В строке раскрывающегося списка предоставляется в верхней части окна кода и два раскрывающихся списков.  
  
## <a name="drop-down-bar-interfaces"></a>Раскрывающийся список интерфейсов  
 В [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], например, раскрывающуюся панель содержит списки для [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] элементов и [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] элементы функции-члены, как показано на следующем рисунке.  
  
 ![DROP&#45;вниз полосы](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Раскрывающийся список  
  
 При реализации раскрывающуюся панель, существует четыре интерфейса роль:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Реализация этого интерфейса позволяет вставить в него содержимое раскрывающейся панелью. Каждой комбинации раскрывающегося списка может содержать обычный текст или затейливого текста (полужирный шрифт, курсив или подчеркнутый), может иметь цвет шрифта текста окна или серым шрифта выделение цветом и при необходимости можно указать небольшое растровое изображение рядом с элементом раскрывающегося списка. Аналогичную <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс, растровые изображения предоставляются в списках изображений. Каждое сочетание раскрывающегося списка может иметь другой образ из списка; Тем не менее каждый образ список должен содержать образы имеют одинаковую высоту. Кроме того, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> метод, можно предоставить подсказки для каждого сочетания.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Вызовите этот интерфейс, чтобы создать или уничтожить раскрывающейся панелью для окна кода. Этот интерфейс может также использоваться для определения, раскрывающейся панелью уже добавлен ли в окне кода, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод. Вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Вызовите этот интерфейс для взаимодействия непосредственно с раскрывающейся панелью. Этот интерфейс можно использовать для принудительного обновления в раскрывающемся списке панели содержимого, или чтобы изменить выбор в одном из списков.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Если вы зарегистрировали `ShowDropdownBarOption` в свой ключ реестра службы языка, затем в диспетчер окон кода необходимо отслеживать это событие для синхронизации со предпочтениям пользователя относительно отображение раскрывающейся панелью. Если этот параметр не зарегистрирован в ваш ключ службы языка, то этот параметр для отображения или скрытия раскрывающейся панелью отключен на **параметры** меню.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Присоединить раскрывающейся панелью окна кода  
 Чтобы присоединить раскрывающейся панелью окна кода при его создании, языковой службы должен быть соединен в раскрывающемся списке строки, если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> вызывается метод. Если в вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод указывает, что раскрывающейся панелью еще не существует, а затем вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Для доступа к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> интерфейс, вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> возвращенного указателя вам при вашей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> реализация была присоединена.  
  
## <a name="see-also"></a>См. также  
 [Настраивать код windows с помощью предыдущих версий API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Поддержка панели навигации в языковой службы прежних версий](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)