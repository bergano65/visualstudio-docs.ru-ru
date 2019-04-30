---
title: Задание фонового изображения схемы
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e79a7fd37bd5f2d5298bda6dca7568c6ba4db6ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823961"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Задание фонового изображения схемы
В Visual Studio Visualization and Modeling SDK можно задать фоновое изображение для сгенерированного конструктора с помощью пользовательского кода.

## <a name="setting-the-background-image"></a>Установка фонового изображения

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Установка фонового изображения для сгенерированного конструктора

1. Скопируйте файл изображения, который будет использоваться в качестве фона схемы, в каталог Dsl\Resources текущего проекта.

2. В **обозревателе решений**, щелкните папку Dsl\Resources правой кнопкой мыши, укажите **добавить**, а затем нажмите кнопку **существующий элемент**.

3. В **добавить существующий элемент** диалоговом окне перейдите в папку Dsl\Resources.

4. В **файлы типа** выберите **файлы изображений**.

5. Выберите файл изображения, который был скопирован в каталог и нажмите кнопку **добавить**.

6. Щелкните правой кнопкой мыши Dsl, а затем нажмите кнопку **свойства** чтобы открыть свойства проекта Dsl.

7. На **ресурсы** щелкните **этот проект содержит файл ресурсов по умолчанию. Щелкните здесь, чтобы создать ее.**

8. Добавьте файл изображения в файл ресурсов, перетащив его из **обозревателе решений** в окно ресурсов.

9. Откройте меню "Файл" и выберите параметр для сохранения свойств проекта.

10. Убедитесь, что файл Dsl\Properties\Resources.resx существует и под ним есть файл Resources.Designer.cs.

11. Если файла Resources.Designer.cs нет, выберите файл Resources.resx в **обозревателе решений**.

12. В окне **Свойства** присвойте свойству `Custom Tool` значение `ResXFileCodeGenerator`.

13. В **обозревателе решений**щелкните правой кнопкой мыши проект Dsl, выберите **добавить**и нажмите кнопку **новую папку**.

14. Назовите папку **Custom**.

15. Щелкните папку Custom правой кнопкой мыши **добавить**и нажмите кнопку **новый элемент**.

16. В **Добавление нового элемента** отображаемое в диалоговом окне **шаблоны** выберите **файл кода**.

17. В **имя** введите `BackgroundImage.cs`и нажмите кнопку **добавить**.

18. Скопируйте указанный ниже код в файл BackgroundImage.cs, изменив пространство имен, имя класса схемы и имя ресурса файла изображения.

     Замените "MyDiagramClass" на имя частичного класса схемы, определенное в файле Dsl\GeneratedCode\Diagrams.cs. Узнать правильное пространство имен можно также с помощью файла Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
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

     Дополнительные сведения о настройке модели с помощью программного кода, см. в разделе [перехода и обновления модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>См. также

- [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md)
- [Настройка полей с текстом и изображениями](../modeling/customizing-text-and-image-fields.md)
- [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
