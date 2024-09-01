import phonenumbers
from phonenumbers import geocoder, carrier, timezone
def track_phone_number(phone_number):
    parsed_number = phonenumbers.parse(phone_number)
    location = geocoder.description_for_number(parsed_number, 'en')
    phone_carrier = carrier.name_for_number(parsed_number, 'en')
    phone_timezone = timezone.time_zones_for_number(parsed_number)
    return {
        "Location": location,
        "Carrier": phone_carrier,
        "Timezone": phone_timezone
    }
 if __name__ == "__main__":
    phone_number = input("Enter the phone number with country code (e.g., +14155552671): ")
    info = track_phone_number(phone_number)
    
    print(f"Location: {info['Location']}")
    print(f"Carrier: {info['Carrier']}")
    print(f"Timezone: {info['Timezone']}")
    
