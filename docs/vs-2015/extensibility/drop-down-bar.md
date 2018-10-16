---
title: Раскрывающийся список | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e66dcc1353da2eab6a3fbea365a2a78c564e98d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203376"
---
# <a name="drop-down-bar"></a>Раскрывающийся список
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В строке раскрывающегося списка предоставляется в верхней части окна кода и два раскрывающихся списков.  
  
## <a name="drop-down-bar-interfaces"></a>Раскрывающийся список интерфейсов  
 В [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], например, раскрывающуюся панель содержит списки для [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] элементов и [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] элементы функции-члены, как показано на следующем рисунке.  
  
 ![DROP&#45;вниз полосы](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
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
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Присоединение раскрывающейся панелью в окно кода  
 Чтобы присоединить раскрывающейся панелью окна кода при его создании, языковой службы должен быть соединен в раскрывающемся списке строки, если <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> вызывается метод. Если в вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метод указывает, что раскрывающейся панелью еще не существует, а затем вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Для доступа к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> интерфейс, вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> возвращенного указателя вам при вашей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> реализация была присоединена.  
  
## <a name="see-also"></a>См. также  
 [Настройка кода Windows с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Поддержка панели навигации в языковой службе прежних версий](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

