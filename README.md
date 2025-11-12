
## 🎯 AIM:
To design and develop a **2D Hurdle Game** using **Unity Engine**, where the player character jumps over hurdles and collects coins to score points.



## 🧠 ALGORITHM:
1. Start a new 2D Unity Project.
2. Import and arrange all required game assets — background, track, player, hurdles, and coins.
3. Add the player GameObject with Rigidbody2D and Collider2D components.
4. Create multiple hurdles and coin GameObjects for interaction.
5. Implement scripts to handle player movement, jumping, and score updates.
6. Add a Canvas UI to display the score dynamically.
7. Test, debug, and finalize the game scene.



## 💻 PROGRAM:
Player
```
using System.Collections;
using System.Collections.Generic;
//using System.Numerics;
using UnityEngine;

public class Player : MonoBehaviour
{
    public float speed, jumpforce;
    private Rigidbody2D rb;
    public Score cc;
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float movement = Input.GetAxis("Horizontal");
        transform.position += new Vector3(movement, 0, 0) * speed * Time.deltaTime;
        if (Input.GetKeyDown(KeyCode.Space) && Mathf.Abs(rb.velocity.y) < 0.001f)
        {
            rb.AddForce(new Vector2(0, jumpforce), ForceMode2D.Impulse);
        }

    }

    private void OnTriggerEnter2D(Collider2D other)
    {
        if (other.CompareTag("Destroy"))
        {
            cc.coincount++;
            Destroy(other.gameObject);
        }

    }
}
```
Coin
```
using UnityEngine;
using System.Collections;
using System.Collections.Generic;
using UnityEngine.UI;
public class Score : MonoBehaviour
{
    public int coincount;
    public Text value;
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        value.text = coincount.ToString();
        
    }
}

```
## 🕹️ OUTPUT:
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/1531d018-2ac1-4ac5-8bc6-cac4f04e6073" />



## ✅ RESULT:
The **2D Hurdle Game** was successfully created and executed in **Unity Engine**, allowing the player to jump over hurdles, collect coins, and update the score in real-time.

