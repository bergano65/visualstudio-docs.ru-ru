---
title: Свойства фигур изображений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 79ec5470a8bac83d8e60454c984739f1e520b634
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671388"
---
# <a name="properties-of-image-shapes"></a>Свойства фигур изображений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для указания способа отображения классов домена в созданном конструкторе можно использовать фигуры изображений. Определите фигуру изображения, задав для свойства `Image` класса предопределенный файл изображения. Поддерживаются следующие форматы:

- GIF

- JPG

- . JPEG

- . bmp

- . WMF

- . EMF

- PNG

  По умолчанию файлы ресурсов конструктора, такие как файлы изображений, находятся в папке **Resources** в проекте **DSL** .

  Дополнительные сведения см. [в разделе Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. [в разделе Настройка и расширение предметно-](../modeling/customizing-and-extending-a-domain-specific-language.md)ориентированного языка.

  Формы изображений имеют свойства, перечисленные в следующей таблице.

|свойство;|Описание|Значение по умолчанию|
|--------------|-----------------|-------------|
|Цвет заливки|Цвет заливки этой фигуры.|Белый|
|Режим градиента заливки|Режим градиента заливки этой фигуры.|Горизонтально|
|Имеет точки соединения по умолчанию|Если `True`, фигура будет использовать верхнюю, нижнюю, левую и правую точки соединения в созданном конструкторе.|False|
|Цвет контура|Цвет контура этой фигуры.|Черный|
|Стиль штриха в контуре|Стиль штриха контура этой фигуры (сплошная, Штрихпунктирная, точка, Дашдот, Дашдотдот или пользовательская).|Сплошная|
|Толщина контура|Толщина контура этой фигуры.|0,03125|
|Цвет текста|Цвет, используемый для декораторов текста, связанных с этой фигурой.|Черный|
|Модификатор доступа|Модификатор доступа геометрической фигуры (открытый или внутренний).|Public|
|Настраиваемые атрибуты|Используется для добавления атрибутов в класс исходного кода, созданного из этой фигуры.|\<none>|
|Создает двойное производное|Если `True`, будет сформирован как базовый класс, так и разделяемый класс (для поддержки настройки с помощью переопределений). Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Имеет настраиваемый конструктор|Если `True`, в исходном коде будет предоставлен пользовательский конструктор. Дополнительные сведения см. [в разделе Переопределение и расширение созданных классов](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Модификатор наследования|Описывает тип наследования класса исходного кода, созданного из фигуры изображения (`none`, `abstract` или `sealed`).|Нет|
|Базовая фигура изображения|Базовый класс этой фигуры.|(нет)|
|Название|Имя этой фигуры.|Текущее имя|
|Пространство имен|Пространство имен, связанное с этой фигурой.|Текущее пространство имен|
|Тип подсказки|Место, где определена подсказка (фиксированная, переменная или нет). Если параметр является фиксированным, то в качестве подсказки используется значение свойства `Fixed Tooltip Text`. Если переменная, то подсказка определяется в пользовательском коде.|Нет|
|Примечания|Неформальные примечания, связанные с этой фигурой.|\<none>|
|Начальная высота|Начальная высота этой фигуры в дюймах.|1|
|Начальная ширина|Начальная ширина этой фигуры в дюймах.|1,5|
|Предоставленный цвет заливки как свойство<br /><br /> Предоставленный режим градиента заливки<br /><br /> Раскрытие цвета контура как свойства<br /><br /> Раскрытие стиля штриха в качестве свойства<br /><br /> Доступная толщина контура в качестве свойства<br /><br /> Отображение цвета текста|Если `True`, пользователь может задать указанное свойство фигуры. Чтобы установить это, щелкните правой кнопкой мыши определение фигуры и выберите пункт **добавить предоставленный**.|False|
|Описание|Используется для документирования созданного конструктора.|\<none>|
|Отображаемое имя|Имя, которое будет отображаться в созданном конструкторе для этой фигуры.|\<none>|
|Исправлен текст подсказки|Текст, используемый для фиксированной подсказки.|\<none>|
|Ключевое слово Help|Ключевое слово, используемое для индексации справки F1 для этого элемента.|\<none>|
|Изображение|Путь к файлу изображения, используемому для этой фигуры.|\<none>|

## <a name="see-also"></a>См. также раздел
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
