def getBondPrice(y, face, couponRate, m, ppy=1):
    """
    Calculate the price of a bond.
    
    Parameters:
    y (float): Yield to maturity (YTM) as a decimal.
    face (float): Face value of the bond.
    couponRate (float): Annual coupon rate as a decimal.
    m (int): Maturity in years.
    ppy (int, optional): Payments per year. Default is 1.
    
    Returns:
    float: The bond price.
    """
    coupon = face * couponRate / ppy
    discountRate = y / ppy
    periods = m * ppy
    
    pv_coupons = sum([coupon / (1 + discountRate) ** t for t in range(1, periods + 1)])
    pv_face = face / (1 + discountRate) ** periods
    
    bondPrice = pv_coupons + pv_face
    return bondPrice

# Test values
y = 0.03
face = 2000000
couponRate = 0.04
m = 10

print(getBondPrice(y, face, couponRate, m, 1))  # Annual payments
print(getBondPrice(y, face, couponRate, m, 2))  # Semi-annual payments
