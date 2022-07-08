---
title: Shooting
weight: 9
---


# Shooting - Basic
<iframe width="560" height="315" src="https://www.youtube.com/embed/EwiUomzehKU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Gun Script
{{< highlight csharp "lineNos=table,lineNoStart=1" >}}
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Gun : MonoBehaviour
{
    public GameObject bulletPrefab;
    public Transform launchPosition;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetMouseButtonDown(0))
        {
            if (!IsInvoking("fireBullet"))
            {
                InvokeRepeating("fireBullet", 0f, 0.1f);
            }
        }

        if (Input.GetMouseButtonUp(0))
        {
            CancelInvoke("fireBullet");
        }
    }

    void fireBullet()
    {
        // 1
        GameObject bullet = Instantiate(bulletPrefab) as GameObject;
        // 2
        bullet.transform.position = launchPosition.position;
        // 3
        bullet.GetComponent<Rigidbody>().velocity = transform.parent.forward * 100;
    }

}
{{< /highlight >}}

### Projectile/bullet Script
{{< highlight csharp "lineNos=table,lineNoStart=1" >}}
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SelfDestruct : MonoBehaviour
{
	public float timer = 1f;

	void Update()
	{
		// Using a timer
		//timer -= Time.deltaTime;

		//if (timer <= 0)
		//{
		//	Destroy(gameObject);
		//}
	}

	// Destroy when nolonger visible
	private void OnBecameInvisible()
	{
		Destroy(gameObject);
	}
	// Destroy on collision
	private void OnCollisionEnter(Collision collision)
	{
		Destroy(gameObject);
	}
}
{{< /highlight >}}

# Shooting - Advanced
<iframe width="560" height="315" src="https://www.youtube.com/embed/wZ2UUOC17AY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

