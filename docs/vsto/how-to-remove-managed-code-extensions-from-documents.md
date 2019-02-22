---
title: Практическое руководство. Удаление расширений управляемого кода из документов
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d4b1e315d335215c990329380739f5fbf34997d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625859"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Практическое руководство. Удаление расширений управляемого кода из документов
  Можно программно удалить сборку настройки из документа или книги, которая является частью настройки уровня документа для Microsoft Office Word или Microsoft Office Excel. Затем пользователи могут открывать документы и просматривать содержимое, но любой собственный пользовательский интерфейс (UI), добавляемые в документы не будут отображаться и код не будет выполняться.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Можно удалить с помощью одного из сборки настройки `RemoveCustomization` методы, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Выбор способа зависит от того, требуется ли удалить настройку во время выполнения (то есть, выполнив кода в настройке слово документ или книгу Excel открыт), или если вы хотите удалить настройку из закрытого документа или документа, i s на сервере, который не установлен Microsoft Office.

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Присоединять или отсоединять сборки VSTO в документ Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

## <a name="to-remove-the-customization-assembly-at-runtime"></a>Чтобы удалить сборку настройки во время выполнения

1.  Код настройки, вызовите <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> метод (для Word) или <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> метод (для Excel). Этот метод должен вызываться только после настройки больше не используется.

     Где вызывать этот метод в коде зависит от того, как используются ваши настройки. Например, если клиенты используют функции настройки, пока они не готов к отправке документа другим клиентам, которым требуется только сам документ (но не Настройка), можно создать пользовательский Интерфейс, вызывающий `RemoveCustomization` когда клиент щелкает его. Кроме того Если настройка заполняет документ данными при первом открытии, но не предоставляет других функций, доступных пользователям напрямую, затем можно вызвать RemoveCustomization как можно скорее настройки по завершении инициализации документа.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Чтобы удалить сборку настройки из закрытого документа или документа на сервере

1.  В проекте, который не требует Microsoft Office, таких как консольное приложение или проект Windows Forms, добавить ссылку на *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* сборки.

2.  Добавьте следующий **Imports** или **с помощью** инструкцию в начало файла кода.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3.  Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> и укажите путь к документу решения для параметра.

     В следующем примере кода предполагается, что вы удаляете настройки из документа с именем *WordDocument1.docx* на рабочем столе.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4.  Постройте проект и запустить приложение на компьютере, где вы хотите удалить настройку. На компьютере должен быть средств Visual Studio 2010 для среды выполнения Office.

## <a name="see-also"></a>См. также
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
