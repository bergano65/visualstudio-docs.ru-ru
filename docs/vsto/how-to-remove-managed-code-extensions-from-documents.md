---
title: "Как: удаление расширений управляемого кода из документов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9da75468ae417bd835b457cdbd5219ef9462df1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Практическое руководство. Удаление расширений управляемого кода из документов
  Можно программно удалить сборку настройки из документа или книги, которая является частью настройки уровня документа для Microsoft Office Word или Microsoft Office Excel. Затем пользователи могут открывать документы и просматривать содержимое, но любой собственный пользовательский интерфейс (UI), добавление в документы не будут отображаться и код не будет выполняться.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Можно удалить сборку настройки с помощью одного из методов RemoveCustomization, предоставляемых [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Выбор способа зависит от того, требуется ли удалить настройку во время выполнения (то есть путем выполнения кода в настройке слово документа или книги Excel открыт), или если вы хотите удалить настройку из закрытого документа или документа мной s на сервере, который не установлен Microsoft Office.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как I: выполните присоединение и отсоединение сборки VSTO в документ Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>Чтобы удалить сборку настройки во время выполнения  
  
1.  Код настройки, вызовите <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> метод (для Word) или <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> метод (для Excel). Этот метод должен вызываться только после настройки больше не нужен.  
  
     Где вызвать этот метод в коде зависит от того, как использовать настройку. Например если клиенты используют функции настройки, пока они не готова к отправке документа другим клиентам, которым требуется только сам документ (а не Настройка), можно создать пользовательский Интерфейс, вызывающий RemoveCustomization, когда пользователь его щелкает. Кроме того Если настройка заполняет документ данными при первом открытии, но не предоставляет других функций, доступных пользователям напрямую, затем можно вызывать RemoveCustomization как можно скорее настройки по завершении инициализации документа.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Чтобы удалить сборку настройки из закрытого документа или документа на сервере  
  
1.  В проекте, который не требует Microsoft Office, таких как консольное приложение или проект Windows Forms, добавить ссылку на сборку Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Добавьте следующие **Imports** или **с помощью** инструкции в начало файла с кодом.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> и укажите путь к документу решения для параметра.  
  
     В следующем примере кода предполагается, что вы удаляете настройки из документа с именем **WordDocument1.docx** , находящегося на рабочем столе.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Выполните построение проекта и запустите приложение на компьютере, на которой вы хотите удалить настройку. На компьютере должен быть Visual Studio 2010 Tools для среды выполнения Office.  
  
## <a name="see-also"></a>См. также  
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  