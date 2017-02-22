---
title: "Задание фонового изображения схемы | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Задание фонового изображения схемы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

С помощью пользовательского кода в пакете SDK для визуализации и моделирования в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно установить фоновое изображение для сгенерированного конструктора.  
  
## Установка фонового изображения  
  
#### Установка фонового изображения для сгенерированного конструктора  
  
1.  Скопируйте файл изображения, который будет использоваться в качестве фона схемы, в каталог Dsl\\Resources текущего проекта.  
  
2.  В **Обозревателе решений** щелкните папку Dsl\\Resources правой кнопкой мыши, наведите указатель мыши на пункт **Добавить** и выберите параметр **Существующий элемент**.  
  
3.  В диалоговом окне **Добавление существующего элемента** найдите папку Dsl\\Resources.  
  
4.  В списке**Тип файлов** выберите **Файлы изображений**.  
  
5.  Выберите файл изображения, скопированный ранее в каталог, и нажмите кнопку **Добавить**.  
  
6.  Щелкните Dsl правой кнопкой мыши и выберите пункт **Свойства**, чтобы открыть свойства проекта Dsl.  
  
7.  На вкладке **Ресурсы** нажмите **Этот проект не содержит файл ресурсов, используемый по умолчанию. Щелкните здесь, чтобы создать такой файл.**  
  
8.  Добавьте изображение в файл ресурсов, перетащив его из **Обозревателя решений** в окно ресурсов.  
  
9. Откройте меню "Файл" и выберите параметр для сохранения свойств проекта.  
  
10. Убедитесь, что файл Dsl\\Properties\\Resources.resx существует и под ним есть файл Resources.Designer.cs.  
  
11. Если файла Resources.Designer.cs нет, выберите файл Resources.resx в **Обозревателе решений**.  
  
12. В окне **Свойства** укажите для свойства `Custom Tool` значение `ResXFileCodeGenerator`.  
  
13. В **Обозревателе решений** щелкните проект Dsl правой кнопкой мыши, наведите указатель мыши на пункт **Добавить** и выберите параметр **Новая папка**.  
  
14. Назовите папку Custom.  
  
15. Щелкните папку Custom правой кнопкой мыши, наведите указатель мыши на пункт **Добавить** и выберите параметр **Новый элемент**.  
  
16. В диалоговом окне **Добавление нового элемента** в списке **Шаблоны** выберите **Файл кода**.  
  
17. В поле **Имя** введите `BackgroundImage.cs` и нажмите кнопку **Добавить**.  
  
18. Скопируйте указанный ниже код в файл BackgroundImage.cs, изменив пространство имен, имя класса схемы и имя ресурса файла изображения.  
  
     Замените "MyDiagramClass" на имя частичного класса схемы, определенное в файле Dsl\\GeneratedCode\\Diagrams.cs.  Узнать правильное пространство имен можно также с помощью файла Dsl\\GeneratedCode\\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Дополнительные сведения о настройке модели с помощью программного кода см. в разделе [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## См. также  
 [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)   
 [Настройка текста и полей изображения](../modeling/customizing-text-and-image-fields.md)   
 [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)