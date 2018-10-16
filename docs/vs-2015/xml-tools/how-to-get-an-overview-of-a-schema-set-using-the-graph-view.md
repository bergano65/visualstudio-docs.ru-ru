---
title: 'Практическое: получить общие сведения о наборе схем с использованием представления графика | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 3722af4aef2f56d6da1c2a79840c05edd2a87b65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181367"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Как получить общие сведения о наборе схем с использованием представления графика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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



