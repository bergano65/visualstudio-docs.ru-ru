---
title: "Ошибка MSBuild MSB3190 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3190
**MSB3190: ClickOnce не поддерживает запрошенный уровень выполнения "\<уровень\>".**  
  
 Эта ошибка появляется на компьютерах с операционной системой Windows Vista, когда во встроенном в приложение манифесте контроля учетных записей \(UAC\) указывается, что приложение ClickOnce выполняется с использованием учетных данных администратора.  Для приложения ClickOnce и COM\-взаимодействия без регистрации требуется внешний манифест, в котором указывается, что приложение выполняется от имени текущего пользователя.  
  
 В ClickOnce не применяются уровни выполнения `requireAdministrator` и `highestAvailable`.  Если указать один из этих уровней, появится данное сообщение об ошибке.  Для приложения ClickOnce требуется ключ `asInvoker`, но для него также применим узел без `<requestedExecutionLevel>`, что указывает на виртуализацию файла или реестра \(это означает, что манифест не создается; используется для обеспечения обратной совместимости\).  
  
> [!NOTE]
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Чтобы исправить эту ошибку  
  
-   Создайте внешний манифест контроля учетных записей \(app.manifest\), в котором указывается, что приложение выполняется от имени текущего пользователя \(`asInvoker`\).  
  
     В проектах Visual C\# перейдите на страницу **Приложение** в конструкторе проектов и в списке **Манифест** выберите **Свойства\\app.manifest**.  Дополнительные сведения см. в разделе [Страница "Приложение" в конструкторе проектов \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
     В проектах Visual Basic перейдите на страницу **Приложение** в конструкторе проектов и нажмите кнопку **Просмотреть параметры контроля учетных записей**.  В результате app.manifest откроется для редактирования.  В манифесте измените следующий тег следующим образом:  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     Дополнительные сведения см. в разделе [Страница «Приложение» в конструкторе проектов \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
-   Дополнительные сведения о том, как создать манифест контроля учетных записей и задать уровень выполнения, см. в разделе [Развертывание ClickOnce в Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md).  
  
## См. также  
 [Страница "Приложение" в конструкторе проектов \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница «Приложение» в конструкторе проектов \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Развертывание ClickOnce в Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)