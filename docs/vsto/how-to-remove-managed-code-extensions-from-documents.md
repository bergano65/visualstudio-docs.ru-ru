---
title: "Практическое руководство. Удаление расширений управляемого кода из документов"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "документы [разработка решений Office в Visual Studio], расширение управляемого кода"
  - "расширения управляемого кода [разработка решений Office в Visual Studio], удаление"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Практическое руководство. Удаление расширений управляемого кода из документов
  Разработчик может программным образом удалить сборку настройки из документа или книги, являющейся частью настройки на уровне документа для Microsoft Office Word или Microsoft Office Excel.  Затем пользователи могут открыть документ и просматривать содержимое, но настраиваемый интерфейс пользователя не появится, и код не будет выполняться.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Чтобы удалить сборку настройки, можно использовать один из методов RemoveCustomization, предоставленных средой [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Выбор используемого метода зависит от необходимости удаления настройки во время выполнения \(т.е. путем выполнения кода в настройке с открытым документом Word или книгой Excel\) или настройки из закрытого документа или документа, находящегося на сервере, на котором не установлен пакет Microsoft Office.  
  
 ![ссылка на видео](~/data-tools/media/playvideo.gif "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылке [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Удаление сборки настройки во время выполнения  
  
1.  Откройте код настройки и вызовите метод <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> для Word или метод <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> для Excel.  Этот метод необходимо вызывать только в том случае, если настройка больше не будет использоваться.  
  
     Место вызова метода в коде зависит от использования настройки.  Например, если клиенты используют функции настройки до момента отправки документа другим клиентам, которым требуется только сам документ \(а не настройка\), то разработчик может создать пользовательский интерфейс, вызывающий RemoveCustomization по щелчку мыши.  Если же настройка заполняет документ данными при первом открытии, но не предоставляет других функций, доступных пользователям напрямую, то RemoveCustomization можно вызвать сразу после завершения инициализации документа настройкой.  
  
### Удаление сборки настройки из закрытого документа или документа на сервере  
  
1.  В проекте, который не требует Microsoft Office, например консольное приложение или проект Windows Forms добавьте ссылку на сборку Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Добавьте следующий оператор **Imports** или **using** в верхнюю часть файла кода.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  Вызовите статический метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> класса <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> и укажите путь документа решения для параметра.  
  
     В следующем примере кода предполагается, что настройка удаляется из документа с именем **WordDocument1.docx**, находящегося на рабочем столе.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  Выполните построение проекта и запустите приложение на компьютере, на котором нужно удалить настройки.  Компьютер должен иметь Visual Studio tools для office 2010 установлена среда выполнения.  
  
## См. также  
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  