---
title: Практическое руководство. Вложение расширений управляемого кода в документы
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18ca5e0cbf341f27454377c544e20cd2aba1388f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044268"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Практическое руководство. Вложение расширений управляемого кода в документы
  Можно подключить сборку настройки для существующего документа Microsoft Office Word или книгу Microsoft Office Excel. Документ или книгу можно в любом формате, который поддерживается проекты Microsoft Office и средства разработки в Visual Studio. Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Чтобы прикрепить настройку к документу Word или Excel, используйте <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класса. Так как <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> класс предназначен для запуска на компьютере, который не установлен Microsoft Office, этот метод можно использовать в решениях, которые не имеют отношения к разработке решений Microsoft Office (например, консоли или приложении Windows Forms).

> [!NOTE]
>  Настройки не удастся загрузить, если код ожидает, что элементы управления, которых нет указанного документа.

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Присоединять или отсоединять сборки VSTO в документ Word? ](http://go.microsoft.com/fwlink/?LinkId=136782).

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Для присоединения расширения управляемого кода в документ

1. В проекте, который не требует Microsoft Office, таких как консольное приложение или проект Windows Forms, добавить ссылку на *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* и  *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* сборки.

2. Добавьте следующий **Imports** или **с помощью** инструкции в начало файла кода.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Вызовите статический <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> метод.

     В следующем примере кода используется <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> перегрузки. Эта перегрузка принимает полный путь к документу и <xref:System.Uri> , указывающий расположение манифеста развертывания для настройки, необходимо подключить к документу. В этом примере предполагается, что документ Word с именем **WordDocument1.docx** на рабочем столе, и манифест развертывания, расположенного в папке с именем **публикации** , также находится на рабочем столе.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Постройте проект и запустить приложение на компьютере, где вы хотите применить настройки. На компьютере должен быть в Visual Studio 2010 Tools для среды выполнения Office.

## <a name="see-also"></a>См. также
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
