---
title: "Раскрывающийся список | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7058c0b93cd0ff4afb2a13b625cd7ef034b03699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="drop-down-bar"></a>Раскрывающийся список
В строке раскрывающегося списка предоставляется в верхней части окна кода и два раскрывающихся списков.  
  
## <a name="drop-down-bar-interfaces"></a>Раскрывающийся список интерфейсов  
 В [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], например, раскрывающуюся панель содержит списки для [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] элементов и [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] элементы функции-члены, как показано на следующем рисунке.  
  
 ![DROP &#45; вниз полосы](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Раскрывающийся список  
  
 При реализации раскрывающуюся панель, существует четыре интерфейса важна.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Реализуйте этот интерфейс, чтобы вставить содержимое раскрывающуюся панель. Каждое сочетание раскрывающийся список может содержать обычный текст или правило, понимаем текст (полужирный шрифт, подчеркивание или курсив), может иметь цвет шрифта текста окна или выделена серым цветом, out шрифта выделение цветом и при необходимости можно указать небольшое растровое изображение рядом с элементом раскрывающегося списка. Аналогично <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс, предоставленных растровых изображений в списках изображений. Каждое сочетание раскрывающийся список может содержать список другое изображение; Однако каждый список изображений должен содержать изображения имеют одинаковую высоту. Кроме того, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> метод, чтобы обеспечить всплывающей подсказки для каждого сочетания.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Вызовите этот интерфейс для создания или удаления раскрывающуюся панель окна кода. Этот интерфейс может также использоваться для определения раскрывающуюся панель уже добавлен ли в окне кода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод. Вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Вызовите этот интерфейс для взаимодействия непосредственно с раскрывающуюся панель. Этот интерфейс можно использовать для принудительного обновления в раскрывающемся списке панели содержимого или чтобы изменить выбор в одном из списка полей.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Если вы зарегистрировали `ShowDropdownBarOption` в ключ реестра службы языка затем диспетчера окон ваш код должен отслеживать это событие для синхронизации с предпочтения пользователя по отображение раскрывающуюся панель. Если этот параметр не зарегистрирован в ваш ключ службы языка, то параметр, чтобы показать или скрыть раскрывающуюся панель отключена на **параметры** меню.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Присоединение раскрывающуюся панель в окне кода  
 Чтобы присоединить раскрывающуюся панель окна кода при его создании, языковой службы должен быть соединен в раскрывающемся списке панели при <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> вызывается метод. Если вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод указывает, что раскрывающуюся панель еще не существует, и вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Для доступа к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> интерфейс, вызовите метод <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> указателя, которое возвращается вам вашей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> реализация была присоединена.  
  
## <a name="see-also"></a>См. также  
 [Настройка окна кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Поддержка панели навигации в языковой службе прежних версий](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)