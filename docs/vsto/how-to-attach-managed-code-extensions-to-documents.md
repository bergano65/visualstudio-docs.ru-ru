---
title: "Практическое руководство. Вложение расширений управляемого кода в документы"
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
  - "расширения управляемого кода [разработка решений Office в Visual Studio], присоединение"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Практическое руководство. Вложение расширений управляемого кода в документы
  Сборку настройки можно вложить в существующий документ Microsoft Office Word или в книгу Microsoft Office Excel.  Документ или книга могут иметь любой формат файла, поддерживаемый проектами и средствами разработки Microsoft Office в Visual Studio.  Дополнительные сведения см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Для вложения настройки в документ Word или Excel используйте метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> класса <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Поскольку класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> разработан для выполнения на компьютере, на котором не установлен Microsoft Office, этот метод можно использовать в решениях, которые не связаны с разработкой Microsoft Office напрямую \(например, в консоли или приложении Windows Forms\).  
  
> [!NOTE]  
>  Загрузка настройки прекратится, если в коде ожидаются элементы управления, отсутствующие в указанном документе.  
  
 ![ссылка на видео](~/data-tools/media/playvideo.gif "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылке [How Do I: Attach or Detach a VSTO Assembly from a Word Document?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### Вложение расширений управляемого кода в документ  
  
1.  В проекте, который не требует Microsoft Office, например консольное приложение или проект Windows Forms добавьте ссылку на сборки Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll и Microsoft.VisualStudio.Tools.Applications.Runtime.dll.  
  
2.  Добавьте следующие операторы **Imports** или **using** в верхнюю часть файла кода.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  Вызовите статический метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  
  
     В следующем примере кода используется перегрузка <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.  Эта перегрузка принимает полный путь документа и <xref:System.Uri>, задающий расположение манифеста развертывания для настройки, которая включается в документ.  В этом примере предполагается, что документ Word с именем **ДокументWord1.docx** находится на рабочем столе, а манифест развертывания расположен в папке рабочего стола **Публикация**.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  Выполните построение проекта и запустите приложение на компьютере, на котором нужно применить настройки.  Компьютер должен иметь Visual Studio tools для office 2010 установлена среда выполнения.  
  
## См. также  
 [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  