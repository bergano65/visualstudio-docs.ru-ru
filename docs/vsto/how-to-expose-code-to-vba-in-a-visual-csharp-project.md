---
title: Руководство. предоставление кода коду VBA в проекте C#
description: Сведения о том, как можно предоставить код в проекте Visual C# для Visual Basic для приложений кода (VBA), если требуется взаимодействие между двумя типами кода.
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1df1eed4edec3efdbf93f4effc352b3d02656d04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889412"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>Руководство. предоставление кода коду VBA в проекте Visual C#
  Можно предоставить код в проекте Visual C# для Visual Basic для приложений кода (VBA), если требуется, чтобы два типа кода взаимодействовал друг с другом.

 Процесс Visual C# отличается от процесса Visual Basic. Дополнительные сведения см. [в разделе руководство. предоставление кода VBA в Visual Basic проекте](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Предоставление кода в проекте Visual C#
 Чтобы включить код VBA для вызова кода в проекте Visual C#, измените код так, чтобы он был видимым для COM, а затем задайте для свойства **ReferenceAssemblyFromVbaProject** в конструкторе **значение true** .

 Пошаговое руководство, в котором показано, как вызвать метод в проекте Visual C# из VBA, см. [в разделе Пошаговое руководство. вызов кода из VBA в проекте Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Предоставление кода в проекте Visual C# для VBA

1. Откройте или создайте проект на уровне документа, основанный на документе Word, книге Excel или шаблоне Excel, который поддерживает макросы и уже содержит код VBA.

    Дополнительные сведения о форматах файлов документов, поддерживающих макросы, см. в разделе [объединение VBA и настроек на уровне документа](../vsto/combining-vba-and-document-level-customizations.md).

   > [!NOTE]
   > Эту функцию нельзя использовать в проектах шаблонов Word.

2. Убедитесь, что код VBA в документе разрешен для выполнения без запроса на включение макросов. Чтобы разрешить выполнение кода VBA, расположение проекта Office можно добавить в список надежных расположений в параметрах Центра управления безопасностью для Word или Excel.

3. Добавьте член, который требуется предоставить коду VBA, в открытый класс в проекте и объявите новый член как **открытый**.

4. Примените следующие <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> атрибуты и к классу, который предоставляется VBA. Эти атрибуты делают класс видимым для модели COM, но без создания интерфейса класса.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. Переопределите метод **GetAutomationObject** класса ведущего элемента в проекте, чтобы получить экземпляр класса, который предоставляется коду VBA:

   - Если класс ведущего элемента предоставляется VBA, переопределите метод **GetAutomationObject** , принадлежащий этому классу, и возвратите текущий экземпляр класса.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - Если вы предоставляете доступ к классу, который не является ведущим элементом VBA, переопределите метод **GetAutomationObject** любого ведущего элемента в проекте и возвратите экземпляр класса элемента, не являющегося ведущим. Например, в следующем коде предполагается, что вы предоставляете в VBA класс с именем `DocumentUtilities` .

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     Дополнительные сведения о ведущих элементах см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

6. Извлеките интерфейс из класса, доступ к которому предоставляется VBA. В диалоговом окне **Извлечение интерфейса** выберите открытые члены, которые необходимо включить в объявление интерфейса. Дополнительные сведения см. в разделе [Извлечение интерфейса рефакторинг](../ide/reference/extract-interface.md).

7. Добавьте в объявление интерфейса ключевое слово **Public** .

8. Сделайте интерфейс видимым для COM, добавив следующий <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут в интерфейс.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. Откройте документ (для Word) или лист (для Excel) в конструкторе в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.

    > [!NOTE]
    > Если книга или документ еще не содержат код VBA или если код VBA в документе не является доверенным для выполнения, то при установке свойства **ReferenceAssemblyFromVbaProject** в **значение true** будет получено сообщение об ошибке. Это происходит потому, что в данной ситуации Visual Studio не может изменить проект VBA в документе.

11. Появляется сообщение, в котором следует нажать кнопку **ОК** . Это сообщение напоминает, что при добавлении кода VBA в книгу или документ при запуске проекта из [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] среды код VBA будет потерян при следующей сборке проекта. Это обусловлено тем, что документ в выходной папке построения перезаписывается при каждом построении проекта.

     На этом этапе Visual Studio настраивает проект таким образом, чтобы проект VBA мог вызывать сборку. Visual Studio также добавляет метод с именем `GetManagedClass` в проект VBA. Этот метод можно вызвать из любого места в проекте VBA для доступа к классу, предоставленному VBA.

12. Выполните построение проекта.

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Объединение настроек VBA и параметров на уровне документа](../vsto/combining-vba-and-document-level-customizations.md)
- [Пошаговое руководство. вызов кода из VBA в проекте Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Руководство. предоставление кода коду VBA в Visual Basicном проекте](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
