# ITprogram
// 商家实体
@Entity
@Data
public class Merchant {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String contact;
    @Enumerated(EnumType.STRING)
    private MerchantStatus status; // PENDING, APPROVED, REJECTED
    // 其他字段...
}

// 菜品实体
@Entity
@Data
public class Dish {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private BigDecimal price;
    @ManyToOne
    private Merchant merchant;
    // 其他字段...
}

// 订单实体
@Entity
@Data
public class Order {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    @ManyToOne
    private Merchant merchant;
    @Enumerated(EnumType.STRING)
    private OrderStatus status; // CREATED, PROCESSING, COMPLETED
    // 其他字段...
}
