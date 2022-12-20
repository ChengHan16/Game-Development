
[[30天Unity大破解] 4:碰碰樂(collider篇)](https://ithelp.ithome.com.tw/articles/10235729)

[Preventing multiple collisions on same target](https://answers.unity.com/questions/897505/preventing-multiple-collisions-on-same-target.html)

```C#
private bool hasCollide = false;
  void OnTriggerEnter (Collider other) {
      if (other.gameObject.tag == "Enemy") {
          if(hasCollide == false){
              hasCollide = true;
              other.gameObject.GetComponent<EnemyHealth>().TakeDamage(WeaponDamage);  
          }
      }
  }

```
[Definitive Fix When Your Character Gets STUCK In Ground Tiles (Unity Basics)!](https://www.youtube.com/watch?v=eJik78bWSg0)

[Why is Rigidbody.MovePosition not smooth?](https://forum.unity.com/threads/why-is-rigidbody-moveposition-not-smooth.1128827/)

[2D Movement [Rigidbody vs Transform] Mastery Tutorial Unity (2021 edition)](https://www.youtube.com/watch?v=fcKGqxUuENk)

[How to Get Smooth Movement in Unity's Input System](https://www.youtube.com/watch?v=krA-B8yItc0)

[How to stop Rigidbody2D from getting stuck on corners?](https://answers.unity.com/questions/1725950/how-to-stop-rigidbody2d-from-getting-stuck-on-corn.html)

[How to Get Smooth Movement in Unity's Input System](https://www.youtube.com/watch?v=krA-B8yItc0)





