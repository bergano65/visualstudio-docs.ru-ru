---
title: "Инструменты Visual Studio для Unity. Пошаговое руководство по RaceScene в Azure | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7dc57628774624975cc6ede5bd241f322472bfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="racescene-explanation"></a>Сведения о RaceScene

В RaceScene используются [стандартные активы](https://www.assetstore.unity3d.com/en/#!/content/32351) Unity для определения основных элементов игрового процесса и уровня. В этом разделе важные объекты GameObject и их скрипты будут рассматриваться в том порядке, в котором они располагаются в иерархии RaceScene, как показано на снимке экрана ниже.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

Объект **MultipurposeCameraRig** взят из пакета стандартных активов **Cameras**. Его свойства Inspector настроены так, чтобы камера следовала за автомобилем с подходящей скоростью.

## <a name="levelgeometry"></a>LevelGeometry

Конструкция LevelGeometry — это пустой объект GameObject, используемый для построения уровня. Его дочерние объекты GameObject образуют игровое пространство. Пол, стены, наклонные плоскости и препятствия строятся с помощью конструкций из пакета стандартных активов **Prototyping**.

**Важно заметить**, что для проверки объекта на столкновения, которые регистрируются в Azure, к нему должен быть применен тег **Wall**.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

Конструкция **Car** взята из пакета стандартных активов **Vehicles**. Единственным изменением является добавление компонента скрипта **RecordCrashInfo**.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Этот скрипт проверяет столкновения в `OnCollisionEnter` и заносит их в список. `crashRecordingCooldown` и `crashRecordingMinVelocity` ограничивают ситуации, которые расцениваются в игре как столкновения, чтобы обеспечить набор соответствующих данных.

Когда возникает событие `RaceFinished`, `UploadNewCrashDataAsync` отправляет каждое столкновение из списка в простую таблицу CrashInfo в Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

Уровень имеет четыре объекта GameObject с компонентом скрипта **Checkpoint**. Контрольные точки нужны для того, чтобы игрок не мог завершить гонку, проехав по трассе в обратном направлении. Они также определяют, когда игрок завершает гонку. В этот момент возникает событие `RaceFinished`.

## <a name="invisible-collision"></a>Столкновение с невидимым объектом

Стандартные простые кубы с отключенным компонентом MeshRenderer используются для создания невидимых стен, чтобы игрок не мог покинуть пределы поля. Кроме того, применяется физический материал **Bouncy**, чтобы находящиеся в полете автомобили отскакивали от невидимых стен естественным образом и чтобы игрок не мог столкнуться с невидимой стеной, соскользнуть по ней вниз и приземлиться на видимой стене.

## <a name="recordhighscore"></a>RecordHighScore

Этот скрипт проверяет, поставил ли игрок новый рекорд. Если да, отображается окно `enterNamePopup`, в котором игрок может ввести свое имя и нажать кнопку **Submit** (Отправить).

После отправки имени игрока вызывается `UploadNewHighScoreAsync` и новый рекорд отправляется в простую таблицу HighScoreInfo в Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Дальнейшие действия

* [Сведения о HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
