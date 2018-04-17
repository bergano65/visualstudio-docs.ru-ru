---
title: Задание фонового изображения на схеме | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2af674f1ca5b29e44d2574ad935dfd3ef3cc1867
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setting-a-background-image-on-a-diagram"></a>Задание фонового изображения схемы
С помощью пользовательского кода в пакете SDK для визуализации и моделирования в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно установить фоновое изображение для сгенерированного конструктора.  
  
## <a name="setting-the-background-image"></a>Установка фонового изображения  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Установка фонового изображения для сгенерированного конструктора  
  
1.  Скопируйте файл изображения, который будет использоваться в качестве фона схемы, в каталог Dsl\Resources текущего проекта.  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши папку Dsl\Resources, укажите **добавить**, а затем нажмите кнопку **существующий элемент**.  
  
3.  В **Добавление существующего элемента** диалоговое окно, перейдите к папке Dsl\Resources.  
  
4.  В **файлы типа** выберите **файлы изображений**.  
  
5.  Выберите файл образа, который был скопирован в каталог и нажмите кнопку **добавить**.  
  
6.  Щелкните правой кнопкой мыши Dsl и нажмите кнопку **свойства** откройте свойства проекта Dsl.  
  
7.  На **ресурсов** щелкните **этот проект не содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать его.**  
  
8.  Добавьте файл изображения в файле ресурсов, перетащив его из **обозревателе решений** в окне «Источники».  
  
9. Откройте меню "Файл" и выберите параметр для сохранения свойств проекта.  
  
10. Убедитесь, что файл Dsl\Properties\Resources.resx существует и под ним есть файл Resources.Designer.cs.  
  
11. Если в местоположении Resources.resx отсутствует, щелкните файл Resources.resx в **обозревателе решений**.  
  
12. В **свойства** задайте `Custom Tool` свойства `ResXFileCodeGenerator`.  
  
13. В **обозревателе решений**, щелкните правой кнопкой мыши проект Dsl, укажите **добавить**и нажмите кнопку **новую папку**.  
  
14. Назовите папку **настраиваемый**.  
  
15. Щелкните правой кнопкой мыши пользовательскую папку, выберите пункт **добавить**и нажмите кнопку **новый элемент**.  
  
16. В **Добавление нового элемента** диалогового **шаблоны** выберите **файл кода**.  
  
17. В **имя** введите `BackgroundImage.cs`и нажмите кнопку **добавить**.  
  
18. Скопируйте указанный ниже код в файл BackgroundImage.cs, изменив пространство имен, имя класса схемы и имя ресурса файла изображения.  
  
     Замените "MyDiagramClass" на имя частичного класса схемы, определенное в файле Dsl\GeneratedCode\Diagrams.cs. Узнать правильное пространство имен можно также с помощью файла Dsl\GeneratedCode\Diagrams.cs.  
  
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
  
     Дополнительные сведения о настройке модели с помощью программного кода. в разделе [перехода и обновления модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>См. также  
 [Определение фигуры и соединители](../modeling/defining-shapes-and-connectors.md)   
 [Настройка текста и полей изображения](../modeling/customizing-text-and-image-fields.md)   
 [Навигация по модели и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
