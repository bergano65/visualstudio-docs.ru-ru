---
title: Полоса раскрывающегося списка | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204644"
---
# <a name="drop-down-bar"></a>Раскрывающаяся панель
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Раскрывающийся список находится в верхней части окна кода и содержит два раскрывающихся списка.  
  
## <a name="drop-down-bar-interfaces"></a>Интерфейсные панели с раскрывающимся списком  
 В [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , например, раскрывающийся список содержит списки для функций- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] членов и элементов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , как показано на следующем рисунке.  
  
 ![Удалить&#45;полосы понижения](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Панель раскрывающегося списка  
  
 При реализации раскрывающегося списка существует четыре интерфейса, которые имеют основную важность:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Реализуйте этот интерфейс, чтобы вставить содержимое раскрывающейся панели. Каждое раскрывающийся список может содержать обычный текст или текст в виде обычного текста (полужирный, подчеркнутый или курсивный), может иметь цвет шрифта окна или затененный цвет шрифта, а также может содержать небольшое точечное изображение рядом с раскрывающимся элементом. Как и в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейсе, точечные изображения предоставляются в списках изображений. Каждое сочетание раскрывающегося списка может иметь другой список изображений. Однако каждый список изображений должен содержать изображения одинаковой высоты. Кроме того, с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> метода можно предоставить подсказку для каждого сочетания.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Вызовите этот интерфейс, чтобы создать или уничтожить раскрывающийся список для окна кода. Этот интерфейс также можно использовать для определения того, присоединена ли раскрывающийся список к окну кода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метода. Вызовите метод <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Вызывайте этот интерфейс для непосредственного взаимодействия с раскрывающимся панелью. Этот интерфейс можно использовать для принудительного обновления содержимого полосы раскрывающегося списка или для изменения выбора в одном из списков.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Если вы зарегистрировали `ShowDropdownBarOption` в разделе реестра языковой службы, диспетчер окон кода должен наблюдать за этим событием, чтобы синхронизироваться с параметрами пользователя о том, следует ли отображать раскрывающиеся панели. Если вы не зарегистрируете этот параметр в ключе языковой службы, параметр Показать или скрыть раскрывающийся список будет отключен в меню **Параметры** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Присоединение раскрывающейся панели к окну кода  
 Чтобы прикрепить раскрывающийся список к окну кода при его создании, языковая служба должна подключаться к раскрывающейся панели при <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> вызове метода. Если вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> метода указывает на то, что раскрывающийся список еще не существует, вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Чтобы получить доступ к <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> интерфейсу, вызовите <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> указателя, возвращенного вам при <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> присоединении реализации.  
  
## <a name="see-also"></a>См. также:  
 [Настройка окон кода с помощью API прежних версий](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Поддержка панели навигации в языковой службе прежних версий](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
