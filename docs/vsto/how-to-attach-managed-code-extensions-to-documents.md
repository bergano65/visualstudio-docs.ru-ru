---
title: "Как: вложение расширений управляемого кода в документы | Документы Microsoft"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1653b0e903fd931d5df4b1dcce4dcbd99fbbae37
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Практическое руководство. Вложение расширений управляемого кода в документы
  Можно подключить сборку настройки для существующего документа Microsoft Office Word или книге Microsoft Office Excel. Документ или книгу можно в любом формате, который поддерживается для проектов Microsoft Office и средства разработки в Visual Studio. Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Чтобы добавить настройку в документ Word или Excel, используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса. Поскольку <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс предназначен для запуска на компьютере, который не установлен Microsoft Office, этот метод можно использовать в решениях, которые непосредственно не связаны с разработкой Microsoft Office (например, консоли или приложения Windows Forms).  
  
> [!NOTE]  
>  Настройку будет невозможно загрузить, если в коде ожидаются элементы управления, не имеет указанного документа.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как I: выполните присоединение и отсоединение сборки VSTO в документ Word?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>Присоединение расширений управляемого кода в документ  
  
1.  В проекте Windows Forms или проекта, для которого не требуется Microsoft Office, например в консольном приложении добавьте ссылку на Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll и Microsoft.VisualStudio.Tools.Applications.Runtime.dll сборки.  
  
2.  Добавьте следующие **Imports** или **с помощью** инструкции в начало файла с кодом.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод.  
  
     Следующий пример кода использует <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> перегрузки. Эта перегрузка принимает полный путь к документу и <xref:System.Uri> , указывающий расположение манифеста развертывания для настройки, нужно присоединить к документу. В этом примере предполагается, что документ Word с именем **WordDocument1.docx** на рабочем столе и который манифест развертывания расположен в папке, которая называется **публикации** , также присутствует на рабочем столе.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  Выполните построение проекта и запустите приложение на компьютере, где вы хотите применить настройки. На компьютере должен быть Visual Studio 2010 Tools для среды выполнения Office.  
  
## <a name="see-also"></a>См. также  
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Как: удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  