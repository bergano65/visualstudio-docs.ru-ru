---
title: 'Практическое: получить общие сведения о наборе схем с использованием представления графика | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b7c3d1d9f351e496469e5b13552ec78e1548f5c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572216"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Как получить общие сведения о наборе схем с использованием представления графика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Ознакомьтесь с обзором схемы задать при помощи представления графика](https://docs.microsoft.com/visualstudio/xml-tools/how-to-get-an-overview-of-a-schema-set-using-the-graph-view).  
  
  
В этом разделе описывается использование [представление графика](../xml-tools/graph-view.md) для просмотра общего представления узлов в наборе схем и связях между узлами.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Создание нового XSD-файла и отображение корневого элемента в представлении модели содержимого  
  
1.  Создайте новый файл XML-схемы и сохраните файл под именем Relationships.xsd.  
  
2.  Нажмите кнопку **использование редактора XML для просмотра и изменения базового файла XML-схемы** ссылку в начальном представлении.  
  
3.  Скопируйте образец кода XML-схемы из [образец XML-схемы: связи](../xml-tools/sample-xsd-file-relationships.md) и вставьте его вместо кода, который был добавлен новый XSD-файл по умолчанию.  
  
4.  Щелкните правой кнопкой мыши в редакторе XML и выберите **конструктор представлений**.  
  
5.  Выберите представление графика на панели инструментов XSD.  
  
6.  Выберите **набора схем** узел в обозревателе XML-схем и перетащите узел в представлении графика на область конструктора. Необходимо увидеть все глобальные узлы и стрелочки, соединяющие связанные друг с другом узлы.  
  
     ![Графическое представление](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Щелкните любой узел в области конструктора, и строка навигатора отобразит расположение выбранного узла в наборе схем.  
  
8.  Щелкните правой кнопкой любой узел элемента по любому и выберите пункт **Создание образца XML** Чтобы просмотреть документ экземпляра XML.



