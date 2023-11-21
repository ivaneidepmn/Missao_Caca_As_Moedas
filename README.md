using UnityEngine;

public class PlayerController : MonoBehaviour
{
   
    public float speed = 5f; // Velocidade de movimento
    private int score = 0; // Pontuação do jogador

    void Update()
    {
        // Movimentação do Personagem
        MoveCharacter();
    }

    void MoveCharacter()
    {
        float horizontalInput = Input.GetAxis("Horizontal");
        float verticalInput = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(horizontalInput, 0, verticalInput) * speed * Time.deltaTime;
        transform.Translate(movement);
    }

    void OnTriggerEnter(Collider other)
    {
        // Se colidir com um objeto que tenha a tag "Coin", colete a moeda
        if (other.CompareTag("Coin"))
        {
            CollectCoin(other.gameObject);
        }
    }

    void CollectCoin(GameObject coin)
    {
        // Adicione aqui a lógica de coleta da moeda
        // Por exemplo, você pode aumentar a pontuação e destruir a moeda
     
        score++;
        Debug.Log("Pontuação: " + score);

        Destroy(coin);
    }
}
