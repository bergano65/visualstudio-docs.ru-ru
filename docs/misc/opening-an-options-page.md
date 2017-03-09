---
title: "Открытие страницы параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "открытие страницы параметров"
  - "параметры инструментов"
  - "страница параметров"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Открытие страницы параметров
Страницу параметров можно отобразить программными средствами, чтобы пользователи вашего пакета могли ее настроить во время установки. Чтобы изменить параметры после установки пакета, пользователь по\-прежнему может открыть страницу параметров с помощью диалогового окна **Параметры**.  
  
### Отображение страницы настраиваемых параметров  
  
1.  Создайте страницу параметров. Для получения дополнительной информации см. [Создание страницы параметров](../extensibility/internals/creating-options-pages.md).  
  
2.  Получите <xref:System.Type> страницы параметров, применив ключевое слово `typeof` к имени класса, определяющего страницу параметров.  
  
3.  Вызовите метод <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A>, используя в качестве параметра тип <xref:System.Type> страницы параметров.  
  
     В следующем примере отображается страница параметров с именем **HelloWorldOptions**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### Отображение страницы параметров, определенной в Visual Studio  
  
1.  В подразделе реестра HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\ найдите узел для страницы параметров, которую требуется отобразить, и скопируйте ее идентификатор GUID, который является значением ключа Page.  
  
2.  Создайте экземпляр <xref:System.ComponentModel.Design.CommandID>, имеющий константы <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> и <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> в качестве параметров.  
  
     Таким образом задается диалоговое окно **Параметры**.  
  
3.  Вызовите метод <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A>, используя в качестве параметров экземпляр <xref:System.ComponentModel.Design.CommandID> и строку идентификатора GUID.  
  
     В следующем примере отображается вкладка **Общие** страницы параметров **Текстового редактора**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]