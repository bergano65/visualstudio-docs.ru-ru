---
title: Как присоединить расширения управляемого кода к документам
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
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985980"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Как присоединить расширения управляемого кода к документам
  Сборку настройки можно прикрепить к существующему Microsoft Office документу Word или Microsoft Office книге Excel. Документ или книга могут иметь любой формат файла, поддерживаемый Microsoft Office проектами и инструментами разработки в Visual Studio. Дополнительные сведения см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Чтобы присоединить настройки к документу Word или Excel, используйте метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> класса <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>. Поскольку класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> предназначен для запуска на компьютере, на котором не установлен Microsoft Office, этот метод можно использовать в решениях, которые не связаны непосредственно с разработкой Microsoft Office (например, консоли или приложения Windows Forms).

> [!NOTE]
> Настройка не сможет загрузиться, если код будет задавать элементы управления, отсутствующие в указанном документе.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Присоединение расширений управляемого кода к документу

1. В проекте, который не требует Microsoft Office, например консольное приложение или проект Windows Forms, добавьте ссылку на *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* и  *Сборки Microsoft. VisualStudio. Tools. Applications. Runtime. dll* .

2. Добавьте следующие инструкции **Imports** или **using** в начало файла кода.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Вызовите статический метод <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>.

     В следующем примере кода используется перегрузка <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>. Эта перегрузка принимает полный путь к документу и <xref:System.Uri>, указывающий расположение манифеста развертывания для настройки, которую необходимо присоединить к документу. В этом примере предполагается, что документ Word с именем **WordDocument1. docx** находится на рабочем столе, а манифест развертывания находится в папке с именем **Publish** , которая также находится на рабочем столе.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Выполните сборку проекта и запустите приложение на компьютере, на котором нужно присоединить настройки. На компьютере должна быть установлена среда выполнения средств Visual Studio 2010 для Office.

## <a name="see-also"></a>См. также
- [Управление документами на сервере с помощью класса ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
